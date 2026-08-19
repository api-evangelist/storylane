---
name: storylane-verify-webhook
description: >
  Receive and verify a Storylane demo-session webhook — validate the
  x-storylane-signature HMAC over the raw body, then route the known/unknown
  session payload. Use when building or debugging a Storylane webhook receiver,
  or when signature verification is failing.
api: storylane:storylane-webhooks
surface: webhooks
operations:
  - demo_viewed
generated: '2026-08-13'
method: generated
source: https://docs.storylane.io/integrations/integrations-and-data-flow/webhooks
---

# Verify a Storylane webhook

Storylane POSTs completed demo sessions to a URL you configure under
**Settings → Integration → Webhook → Connect**. Available from the Starter plan
up.

## The signature

Every request carries `x-storylane-signature`: a **base64-encoded HMAC-SHA256**
of the **raw, unparsed request body**, keyed on your Webhook Verification Secret
(found under Settings → Integrations → Webhook).

To verify:

1. Read `x-storylane-signature` from the headers.
2. Take the **raw** body as a string — not the parsed object, not a re-serialized
   one. Any JSON round-trip changes bytes and breaks the HMAC. This is the
   number-one cause of verification failures.
3. HMAC-SHA256 the raw body with the secret.
4. Base64-encode the digest.
5. Compare against the header value.

Return `200` when it matches, `401` when it does not — the status codes
Storylane's own reference receivers use.

## Use a constant-time comparison

Storylane publishes reference implementations in Node.js/Express, Ruby and
Python/Flask. The Ruby example uses `Rack::Utils.secure_compare` and the Python
example uses `hmac.compare_digest`, both constant-time. **The published Node
example compares with `===`, which is timing-unsafe.** If you copied it, replace
it with `crypto.timingSafeEqual` over equal-length buffers.

## Known limitation: no replay protection

The signed material is the body alone. There is **no timestamp in the signature
and no documented replay window**. The signature proves the payload came from
Storylane; it does not prove it is fresh. If replay matters to you, dedupe on the
session `id` field yourself and keep a seen-id window.

## Routing the payload

The `event` field in every published sample is `demo_viewed`. Two variants:

- **Known session** — `lead` is an object with `id`, `email`, `first_name`,
  `last_name`, `lead_source`, `client_source`, `client_tracking_id`.
- **Unknown session** — `lead` is `null`. `buyer_reveal` may still resolve the
  company (`company_name`, `company_domain`, revenue and employee ranges,
  `confidence_score`).

Always null-check `lead` before dereferencing it. You control which variants you
receive: the webhook config offers all sessions, or known lead/account only.

Engagement fields worth routing on: `completion` (percent), `time_spent`
(seconds), `intent_level`, `checklist_completed`, `cta_opened`, plus `location`,
`referers` and `utm_params`. Full field list in
`asyncapi/storylane-webhooks.yml`; entity shapes in
`data-model/storylane-data-model.yml`.

## Watch out for

- **`buyer_reveal` is metered.** Account reveal is quota'd per plan — 250/month
  on Starter, 2,500 on Growth, 10,000 on Premium. Once exhausted, expect the
  reveal to stop resolving; the webhook still fires.
- **Timestamps carry non-UTC offsets.** `viewed_at` looks like
  `2026-05-20T03:27:29.246-07:00`. Parse the offset; do not assume Z.
- **No delivery guarantees are published** — no documented retry policy, backoff,
  delivery log or replay UI. Treat delivery as at-most-once unless you have
  confirmed otherwise with Storylane, and make your handler idempotent on
  session `id`.
