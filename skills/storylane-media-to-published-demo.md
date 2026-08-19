---
name: storylane-media-to-published-demo
description: >
  Turn screenshots or a screen recording into a published Storylane interactive
  demo — convert the media, wait for processing, add any missing steps, set
  title/branding/gating, and publish. Use when someone has a recording or images
  and wants a demo out of them.
api: storylane:storylane-mcp
surface: mcp
endpoint: https://identity.storylane.io/mcp
operations:
  - convert_images_to_demo
  - convert_video_to_demo
  - get_demo_status
  - add_step
  - list_voices
  - update_demo_settings
  - publish_demo
generated: '2026-08-13'
method: generated
source: https://docs.storylane.io/integrations/integrations-and-data-flow/mcp
---

# Build and publish a Storylane demo from media

Mirrors the "Create a launch demo from media" and "Convert a screen recording
into a demo" workflows Storylane publishes on its MCP documentation page.

## Before you start

- Endpoint `https://identity.storylane.io/mcp`, OAuth, scope `demos_write`.
- Confirm the active workspace with `list_workspaces` / `switch_workspace` before
  creating anything. A demo created in the wrong workspace has to be rebuilt.

## Steps

1. **Convert the media.**
   - Images or screenshots → `convert_images_to_demo`.
   - A screen recording or video → `convert_video_to_demo`.
2. **Poll for completion.** Call `get_demo_status`. This step is not optional —
   conversion is asynchronous, and every later call will operate on an
   incompletely processed demo if you skip it. Back off between polls; there are
   no rate-limit headers to guide you.
3. **Fill the gaps.** `add_step` for any text, hotspot or tooltip step the
   conversion missed.
4. **Choose narration if the demo needs it.** `list_voices` returns available AI
   voices with language, voice id and preview URL.
5. **Set the wrapper.** `update_demo_settings` for title, description, branding,
   gating and embed settings. Gating is what determines whether this demo
   captures leads at all.
6. **Publish.** `publish_demo`.
7. **Distribute.** Hand off to `create_link` (see
   `storylane-personalized-demo-for-account`) or embed it — the embed contract is
   in `components/storylane-components.yml`.

## Watch out for

- **Retries can duplicate.** No idempotency key exists on any Storylane surface.
  A timed-out `convert_video_to_demo` retried blindly can produce two demos.
  Check `list_demos` before retrying a conversion.
- **Processing status has no REST equivalent.** `get_demo_status` is MCP-only —
  the documented REST demo object exposes `status` (published / amended) and
  `published_at` but nothing about processing. Do not try to substitute a REST
  poll.
- **Turn on LLM-Friendly if this demo should be discoverable.** Storylane's embed
  panel has an LLM-Friendly toggle (Share → Embed) that makes demo content
  readable by LLMs and search engines. An embedded demo without it is opaque to
  crawlers and to agents.
- **If the demo will be embedded**, the host page can subscribe to
  `storylane-demo-event` postMessage events (`demo_open`, `step_view`,
  `demo_finished`, `lead_identify`, `open_external_url`) — catalogued in
  `asyncapi/storylane-webhooks.yml`.
