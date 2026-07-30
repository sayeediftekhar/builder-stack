# builder-stack

A portable, installable reference system for starting and governing any
software project built with Claude Code. It is not a project you build — it
is the methodology you install *into* the projects you build.

The stack has three layers. They do not overlap. They stack.

## Layer 1 — Harness (Keel)
**Controls how work flows.** Routes every task by danger level, enforces
ceremony for high-risk work, gates commits, and never lets the agent
self-approve consequential changes.
→ https://github.com/sayeediftekhar/Keel

## Layer 2 — Context (lean-context)
**Controls what the agent sees.** Tiers project knowledge, indexes it, and
fetches on demand so the context window stays lean and the harness's
instructions never get diluted.
→ https://github.com/sayeediftekhar/lean-context

## Layer 3 — Architecture (Systems Thinking)
**Controls how you design.** The seven-rung framework — boundaries,
contracts, change surfaces, structure, scale, feedback, sequencing — that
you reason through *before* building. Lives in
[`docs/SYSTEMS_THINKING_FRAMEWORK.md`](docs/SYSTEMS_THINKING_FRAMEWORK.md).

## When to use each layer
- **Systems Thinking** — at project start and at every design decision. Used
  by you (architect chat), not loaded into Claude Code.
- **lean-context** — once, when you set up a repo. Produces the tiered
  structure the agent reads.
- **Keel** — on every task, forever. The runtime harness.

Each layer depends on the one below being in place: architecture tells the
tiers what is load-bearing; lean context keeps the window clear so the
harness stays sharp; the harness makes the architecture automatic.

## Quick Start — install the full stack on a new project
1. **Install Keel** as a submodule at `.claude/skills`, add its routing line
   to `CLAUDE.md`.
2. **Run lean-context** — fetch `DIRECTIVE.md`, execute it, archive it.
3. **Architect** — reason through the seven rungs, write `docs/ARCHITECTURE.md`.
4. **Wire it together** — fill the templates in [`templates/`](templates/) and
   work down [`setup/NEW_PROJECT_CHECKLIST.md`](setup/NEW_PROJECT_CHECKLIST.md).

Start with [`setup/STACK.md`](setup/STACK.md) for the one-page overview, or
[`docs/INTEGRATION_GUIDE.md`](docs/INTEGRATION_GUIDE.md) for the full wiring.
