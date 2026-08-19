---
name: storylane-personalized-demo-for-account
description: >
  Prepare an account-specific Storylane demo before a sales call — find the right
  demo, create an AI-personalized variant for the company or persona, publish it,
  and generate a trackable share link. Use when someone asks to personalize a
  demo for a prospect or produce a link for a meeting.
api: storylane:storylane-mcp
surface: mcp
endpoint: https://identity.storylane.io/mcp
operations:
  - list_demos
  - get_demo
  - personalise_demo
  - publish_demo
  - create_link
generated: '2026-08-13'
method: generated
source: https://docs.storylane.io/integrations/integrations-and-data-flow/mcp
---

# Personalize a Storylane demo for one account

Mirrors the "Prepare a personalized demo before a call" workflow Storylane
publishes on its MCP documentation page. Note the British spelling of
`personalise_demo` — that is the provider's tool name and it is the one that
works.

## Before you start

- OAuth against `https://identity.storylane.io` (PKCE `S256`); the endpoint is
  `https://identity.storylane.io/mcp`.
- This flow **writes**. It needs the `demos_write` scope. In ChatGPT, write
  actions additionally require Developer Mode, which Storylane documents as beta
  and limited to Business and Enterprise plans; read-only tools work on all
  plans. In Claude, a company account needs an admin to add the connector.
- Confirm the active workspace before writing anything.

## Steps

1. **Find the source demo.** `list_demos`, then `get_demo` on the candidate to
   confirm its chapters and steps actually cover the use case. Read before you
   copy — a personalized variant of the wrong demo is worse than no demo.
2. **Create the variant.** `personalise_demo` with the company, persona or
   context. This creates a **new demo variant** with AI-adapted content; it does
   not modify the original.
3. **Publish it.** `publish_demo`. A variant that is not published has no share
   link worth sending.
4. **Create the tracked link.** `create_link` with the viewer variables you want
   on the URL. The link object is where the access controls live — `passcode`,
   `expires_at`, `email_required`, `email_confirmation_required` and
   `whitelist_email_domains`. Set them deliberately; the default link is open.
5. **Hand back the URL** and say what protections are on it.

## Know the difference before you pick a tool

Storylane's own FAQ draws this line and it is the single most common mistake:

- `personalise_demo` creates a **new demo variant** with AI-adapted content.
- `create_link` adds **dynamic viewer variables to a tracked URL**. It does not
  modify the demo at all.

If the ask is "put their name and logo on it", a link token may be enough and is
far cheaper than a variant. If the ask is "make the content speak to their
industry", you need the variant.

## Watch out for

- **No idempotency keys.** Storylane documents none, on any surface. If
  `personalise_demo`, `publish_demo` or `create_link` times out, a blind retry
  can create a duplicate variant or a duplicate link. Re-read with `list_demos` /
  `list_links` before retrying.
- **Retiring a link is not covered.** The published tool set has `create_link`
  and `update_link` but no delete. Use `update_link` to set `expires_at` when a
  link should stop working.
- **Link URLs are workspace-subdomained** (`https://<workspace>.storylane.io/share/<slug>`),
  so do not construct one by hand — always use the URL the API returns.
