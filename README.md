# charly-hermes

The `charly-hermes` family — the Hermes AI-agent image and layer skills.

The `charly-hermes` candy is a **concept candy**: it ships no install content
and owns the `hermes` family of `skill:` entities whose names have no namesake
candy. It currently carries four entities:

- `hermes-layer` — the Hermes agent candy (self-improving agent by Nous
  Research with voice, messaging, and tool-calling; LLM/MCP auto-config).
- `hermes-full-layer` — the `hermes-full` metalayer: Hermes plus AI CLIs
  (Claude Code, Codex, Gemini), dev tools, and DevOps tools.
- `hermes-playwright-layer` — Playwright Chromium for Hermes on Fedora.
- `playwright-layer` — the standalone `playwright` candy (browser automation).

Two further `hermes`-family skills are owned by sibling repos: `hermes` in
`opencharly/pod-hermes` and `hermes-playwright` in
`opencharly/layer-hermes-playwright`. `candy/plugin-marketplace` regenerates the
standalone [opencharly/marketplace](https://github.com/opencharly/marketplace)
corpus from these entities, so the skills are authored here and projected there.

## What it provides

| Property | Value |
|---|---|
| Layer / candy | `charly-hermes` (concept candy) |
| Install content | none — a `true` no-op `plan:` |
| Owns | 4 `skill:` entities: `hermes-layer`, `hermes-full-layer`, `hermes-playwright-layer`, `playwright-layer` |
| Projected to | `marketplace/hermes/skills/` |
| Service / port | none |

## How to use it

This repo is consumed as a **skill source**, not as an image layer. Edit the
`skill:` entities in `charly.yml`; the marketplace regeneration projects them
into `/charly-hermes:*` pages. To reference the repo directly, compose it in a
box. A box is a `candy:` node that carries the box's `base:` image and a nested
`candy:` list of layer refs (the nested `candy:` is the composition list; the
outer `candy:` is the box body):

```yaml
my-box:
  candy:                  # the box body (an IMAGE is a `candy:` node carrying `base:`)
    base: fedora          # the box's base image
    candy:                # the box's composition list
      - '@github.com/opencharly/layer-charly-hermes:v2026.243.2102'
```

The Hermes agent itself is deployed through the `hermes` box, which composes the
`hermes` candy from `opencharly/pod-hermes`; the `hermes-layer` skill here
documents that candy's behaviour.

## Layout

- `charly.yml` — the `charly-hermes:` concept candy entity plus four `skill:`
  entities (`hermes-full-layer`, `hermes-layer`, `hermes-playwright-layer`,
  `playwright-layer`).
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — this user overview.

## Related

- Owning skill: `/charly-hermes:hermes-layer`
- Authoring reference: `/charly-image:layer`
- Hermes box: `/charly-hermes:hermes` (in `opencharly/pod-hermes`)
- Playwright sibling: `opencharly/layer-hermes-playwright`
- [`opencharly/marketplace`](https://github.com/opencharly/marketplace) — the projected corpus
- [`opencharly/charly`](https://github.com/opencharly/charly) — the charly CLI and image builder
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella
