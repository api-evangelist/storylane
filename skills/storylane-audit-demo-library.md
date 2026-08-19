---
name: storylane-audit-demo-library
description: >
  Audit a Storylane workspace's published demo library by engagement — list every
  published demo, pull its analytics, rank worst to best, and recommend update,
  personalize or retire for each. Use when someone asks which demos are working,
  which are stale, or what to clean up.
api: storylane:storylane-mcp
surface: mcp
endpoint: https://identity.storylane.io/mcp
operations:
  - list_workspaces
  - switch_workspace
  - list_demos
  - get_demo_analytics
generated: '2026-08-13'
method: generated
source: https://docs.storylane.io/integrations/integrations-and-data-flow/mcp
---

# Audit a Storylane demo library

Mirrors the "Audit your demo library" workflow Storylane publishes on its MCP
documentation page. Every tool named here is a real, provider-published Storylane
MCP tool.

## Before you start

- The Storylane MCP server is at `https://identity.storylane.io/mcp` and it is
  **OAuth-gated**. An unauthenticated `tools/list` returns
  `401 {"error":"unauthorized","error_description":"Bearer token required"}` with
  `WWW-Authenticate: Bearer realm="Storylane MCP"`. Complete the authorization
  code flow against issuer `https://identity.storylane.io` (PKCE `S256`) first.
- Read access needs the `demos_read` scope; the analytics calls need
  `analytics_read`. See `scopes/storylane-scopes.yml`.
- Every tool is scoped to the **active workspace** and to the authorizing user's
  own permissions. There is no cross-workspace read.

## Steps

1. **Confirm the workspace.** Call `list_workspaces`. If the user's intended
   workspace is not the active one, call `switch_workspace`. Do not assume — the
   whole audit is silently wrong if it runs against the wrong workspace.
2. **List the demos.** Call `list_demos`. It supports filtering and search, but
   Storylane publishes no parameter names, so read them from the live tool's
   `inputSchema` rather than guessing.
3. **Pull analytics per demo.** Call `get_demo_analytics` for each demo id. It
   returns views, unique visitors, session duration, CTA clicks, click-through
   rate and completion rate.
4. **Rank.** Order worst to best on the metric the user actually cares about.
   Completion rate and views over a stated window are the two the docs use.
5. **Recommend.** For each low performer, propose one of update, personalize
   (`personalise_demo`) or retire — and say why, citing the number.

## Watch out for

- **Pagination is undocumented.** `list_demos` returns a bare array with no
  cursor, page or total field anywhere in Storylane's published response shapes.
  You cannot prove a list is complete. Say so in the output rather than implying
  the audit covered everything.
- **No rate-limit headers.** Storylane emits no `X-RateLimit-*`, `RateLimit-*` or
  `Retry-After` on any observed response, and publishes no request limits. Pace
  the per-demo analytics loop conservatively on a large library.
- **Correlate failures with `x-request-id`.** Every Storylane response carries a
  UUID `x-request-id`. Capture it on any error — the REST API is
  support-provisioned, so that id is what support will ask for.
