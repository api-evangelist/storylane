# Storylane

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Storylane is an interactive demo platform that enables sales and marketing teams to build and share self-serve product walkthroughs, embedded demos, and demo galleries without engineering involvement. The platform offers an External REST API for Enterprise customers to programmatically manage published demos, generate secure shareable links with passcodes and expiration dates, and personalize demo experiences via email parameters. Storylane also provides webhooks, cross-frame events, and 30-plus native integrations with CRM, marketing automation, and analytics tools to connect demo engagement data with existing GTM workflows. Its widest programmatic surface is not REST but a first-party hosted Model Context Protocol server at identity.storylane.io/mcp, secured with OAuth 2.0 dynamic client registration and PKCE, exposing 22 documented tools for demo creation from media, AI personalization, publishing, hubs, voices, analytics, leads and accounts to Claude, ChatGPT and other MCP clients.

**Areas:** Interactive Demos · Product Walkthroughs · Sales Enablement · Marketing · Demo Analytics · Demo Automation · Buyer Hub · Sales · MCP · Agent Tools · Webhook · Embed

## Storylane on APIs.io

Everything profiled for Storylane is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/storylane/](https://apis.io/providers/storylane/)** — or go straight to one of the APIs or properties below.

### APIs (4)

- [Storylane External API](https://apis.io/apis/storylane/storylane-external-api/) — The Storylane External API allows Enterprise plan customers to programmatically list published demos, retrieve demo details including chapters and steps,…
- [Storylane MCP Server](https://apis.io/apis/storylane/storylane-mcp/) — Storylane's first-party hosted Model Context Protocol server, the widest programmatic surface the company operates. It exposes 22 documented tools covering…
- [Storylane oEmbed API](https://apis.io/apis/storylane/storylane-oembed-api/) — A public, unauthenticated oEmbed 1.0 provider endpoint that resolves any Storylane demo share URL into a rich embed response containing the demo title,…
- [Storylane Webhooks and Demo Events](https://apis.io/apis/storylane/storylane-webhooks/) — Storylane's event surface, in two channels. Outbound HTTPS webhooks deliver completed demo sessions to a customer endpoint, signed with a base64 HMAC-SHA256…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Storylane Webhooks](https://apis.io/asyncapis/storylane/storylane-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [Storylane MCP](https://apis.io/servers/storylane/storylane-mcp/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Storylane Context](https://apis.io/jsonld/storylane/storylane-context/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Storylane Authentication](https://apis.io/security/storylane/storylane-authentication/)
- [Storylane Domain Security](https://apis.io/security/storylane/storylane-domain-security/)
- [Storylane Trust Center](https://apis.io/security/storylane/storylane-trust-center/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Storylane Scopes](https://apis.io/scopes/storylane/storylane-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Storylane Plans Pricing](https://apis.io/plans/storylane/storylane-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Storylane Rate Limits](https://apis.io/rate-limits/storylane/storylane-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Storylane Finops](https://apis.io/finops/storylane/storylane-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.storylane.io)
- [Documentation](https://docs.storylane.io)
- [Getting started](https://docs.storylane.io/welcome-to-storylane)
- [API reference](https://docs.storylane.io/integrations/integrations-and-data-flow/external-api)
- [Pricing](https://www.storylane.io/pricing)
- [Sign up](https://app.storylane.io/register)
- [Blog](https://www.storylane.io/blog)
- [Terms of service](https://www.storylane.io/terms-of-service)
- [Privacy policy](https://www.storylane.io/privacy-policy)
- [Status](https://status.storylane.io)

## API Evangelist rating

**Kin Score 63.8** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 80.0 |
| Contract quality | 50.6 |
| Contract governance | 18.2 |
| Operational transparency | 76.3 |
| Developer ergonomics | 51.8 |
| Access clarity | 85.5 |

**Agent readiness 42.1** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | — |
| MCP Server | documented (partial credit) |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | — |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | — |
| Dynamic Client Registration | yes |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | na |

**Regulatory alignment 39.2** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/storylane/](https://apis.io/providers/storylane/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Storylane: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/storylane/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
