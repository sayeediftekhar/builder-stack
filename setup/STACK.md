# The Stack — one page

Three layers govern any project built with Claude Code. They do not overlap.
They stack.

## The three layers

| Layer | Name | Repo | Controls |
|-------|------|------|----------|
| 1 | **Harness** — Keel | https://github.com/sayeediftekhar/Keel | How work flows |
| 2 | **Context** — lean-context | https://github.com/sayeediftekhar/lean-context | What the agent sees |
| 3 | **Architecture** — Systems Thinking | this repo (`docs/SYSTEMS_THINKING_FRAMEWORK.md`) | How you design |

## What each layer controls
- **Layer 1 — Harness (Keel).** Governs *how work flows*: routes each task by
  danger level, enforces ceremony for high-risk work, gates commits, never
  self-approves consequential changes.
- **Layer 2 — Context (lean-context).** Governs *what the agent sees*: tiers
  and indexes project knowledge, fetches on demand, never front-loads — so the
  window stays lean and the harness stays sharp.
- **Layer 3 — Architecture (Systems Thinking).** Governs *how you design*: the
  seven rungs — boundaries, contracts, change surfaces, structure, scale,
  feedback, sequencing.

## The rule
They don't overlap — they stack. Each depends on the one below being in
place: architecture tells the context tiers what is load-bearing; lean context
keeps the window clear so the harness's instructions stay undiluted; the
harness makes the architecture automatic, every session.

## When each is invoked
- **Systems Thinking** — in your architect chat at project start and at every
  design decision (it produces `docs/ARCHITECTURE.md`).
- **lean-context** — once per repo, via `DIRECTIVE.md`, at setup.
- **Keel** — via the `keel-v2` skill on every task, forever.

Full setup: `setup/NEW_PROJECT_CHECKLIST.md`. Full wiring:
`docs/INTEGRATION_GUIDE.md`.
