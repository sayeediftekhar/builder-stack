# Keel + lean-context + Systems Thinking — Integration Guide

The master wiring document for the stack: what each piece does, why they stay
separate, and how a new project installs all three as one coherent system.
(Condensed from the source guide to fit the repo's 200-line limit; the full
substance is preserved.)

---

## What each repo actually does

**Keel** (`sayeediftekhar/Keel`) is a **harness** — it governs *how work
flows*. It routes tasks by danger level, enforces ceremony for high-risk
work, gates commits, and never lets the agent self-approve consequential
changes. Operates at the **task level**: every task enters Keel, gets a rigor
record, and follows the appropriate lane.

**lean-context** (`sayeediftekhar/lean-context`) is a **context discipline**
— it governs *what the agent sees*. It tiers project knowledge, indexes it,
and fetches on demand, never front-loading. Operates at the **session
level**: every session starts lean and loads the minimum.

**Systems Thinking Framework** is a **structural philosophy** — it governs
*how the system is designed*: boundaries, contracts, change surfaces,
coupling, feedback, sequencing. Operates at the **architecture level**: every
design decision is tested against it.

These three operate at different levels and do non-overlapping jobs. They are
not duplicates — they are layers.

---

## Should you combine them? No — and yes.

Do **not** merge them into one repo. They serve different purposes, are used
at different times, and by different actors (Keel for Claude Code;
lean-context for the repo structure; Systems Thinking for you the architect).
Merging would create the exact bloat they each fight.

**But** they must know about and reference each other, so a new project can
install all three without gaps or conflicts. The right model: **three
independent repos, one install sequence, one README that explains the stack.**

---

## The unified stack

```
┌─────────────────────────────────────────────────────┐
│  LAYER 3 — Architecture (Systems Thinking)          │
│  What you design before building anything           │
│  Lives in: your head + docs/ARCHITECTURE.md         │
│  Invoked: at project start, at every design decision│
├─────────────────────────────────────────────────────┤
│  LAYER 2 — Context (lean-context)                   │
│  What the agent sees each session                   │
│  Lives in: repo structure (tiers 1-2-3)             │
│  Invoked: DIRECTIVE.md run once per repo setup      │
├─────────────────────────────────────────────────────┤
│  LAYER 1 — Harness (Keel)                           │
│  How work flows task by task                        │
│  Lives in: .claude/skills/ as git submodule         │
│  Invoked: keel-v2 skill on every task              │
└─────────────────────────────────────────────────────┘
```

Each layer depends on the one below. Keel without lean context → the window
bloats and Keel's instructions dilute. Lean context without good
architecture → the tiers don't know what's load-bearing. Architecture
without a harness → just theory.

---

## Setting up a new project with all three

### Step 1 — Install the harness (Keel)
```bash
git submodule add https://github.com/sayeediftekhar/Keel .claude/skills
git submodule update --init --recursive
```
Installs `keel-v2` and `lazy-loop` under `.claude/skills/skills/`; Claude Code
discovers them automatically. Add to `CLAUDE.md`:
```
Route every task through keel-v2 before planning or writing code.
```

### Step 2 — Install the context discipline (lean-context)
```bash
curl -O https://raw.githubusercontent.com/sayeediftekhar/lean-context/main/DIRECTIVE.md
```
Then tell Claude Code: *"Read DIRECTIVE.md and execute it. Stop at each STOP
for my approval."* It audits the repo and produces the three-tier structure:
- **Tier 1** — lean `CLAUDE.md` (aim under ~100 lines: rules + authorities index + Keel
  routing line; if it grows, push operating-model prose to docs/)
- **Tier 2** — Keel skills on the bookshelf (installed in Step 1)
- **Tier 3** — `docs/` for deep reference, fetched on demand

Archive `DIRECTIVE.md` after it runs — it's a one-time setup tool.

### Step 3 — Establish the architecture layer (Systems Thinking)
Before any code, create `docs/ARCHITECTURE.md` — the project-specific
application of the seven rungs. Answer and record: load-bearing pieces (built
thin but correct first), the module map (one job per module), the Iron Laws,
the change-surface decisions (volatile vs stable + separation mechanism), and
the sequencing plan (Phase 0, then vertical slices in dependency order). Use
`templates/ARCHITECTURE.md`. This doc lives in `docs/` and is referenced from
the authorities index — fetched on demand, never standing.

### Step 4 — Wire them together in CLAUDE.md
`CLAUDE.md` after setup carries: a **truth order** line (live DB/schema/data
> code > prose docs); an **operating model** (route through keel-v2; one task
= one PR = one context boundary; plan before code; verify in the real
environment; load on demand); the **Iron Laws**; a **session start** line
(read CONTEXT.md, check git status, read the spec, do NOT preload
docs/); the **authorities index** table; and a single `@docs/INDEX.md` eager
import — a ~30-line pointer table, the only eager load. Everything else is
fetched when a task needs it. Use `templates/CLAUDE.md`.

---

## Managing an ongoing project

**Each session** Claude Code reads `CLAUDE.md` (routing → Keel, Iron Laws,
authorities index, the `@docs/INDEX.md` import), then reads `CONTEXT.md`
as its first action. That is the entire standing load.

**Each task** (1) keel-v2 scans danger surfaces and recommends a rigor level,
stopping for your confirmation; (2) you confirm HEAVY or LIGHT (or override
with a recorded reason); (3) HEAVY: verify-fact → plan → your review → build →
review → real-environment check → gated commit; LIGHT: build → tripwire
review → real-environment check → commit.

**After each task** run the three feedback signals — *change radius* (touched
more files than expected?), *explanation test* (still one sentence per
module?), *surprise test* (anything break that shouldn't have?). File any hit
as its own refactoring task. Update `CONTEXT.md` and `LEARNINGS.md`
before ending.

**Every 5–10 features** review `docs/ARCHITECTURE.md`: are boundaries holding?
has a module grown a second job? is volatile tangling with stable? File issues
as explicit refactoring tasks, separate from feature work.

---

## The framework as an invokable reference

`SYSTEMS_THINKING_FRAMEWORK.md` belongs in this methodology repo — not in
every project. You pull it into your architect chat at project start and ask:
*"Given this project, how do the seven rungs apply? What's load-bearing? What
are my module boundaries and Iron Laws?"* That conversation produces
`docs/ARCHITECTURE.md`, which you hand to Claude Code via the authorities
index. You don't load the framework into Claude Code — it's a thinking tool
for you, not a runtime instruction.

---

## What lives where — the definitive map

| What | Repo | Used by | When |
|------|------|---------|------|
| `keel-v2` skill | `sayeediftekhar/Keel` | Claude Code | Every task |
| `lazy-loop` skill | `sayeediftekhar/Keel` | Claude Code | Token optimization |
| `DIRECTIVE.md` | `sayeediftekhar/lean-context` | Claude Code | Once per repo setup |
| `PLAYBOOK.md` | `sayeediftekhar/lean-context` | You | Reading the why |
| `SYSTEMS_THINKING_FRAMEWORK.md` | This repo | You (architect chat) | Project start, design decisions |
| `docs/ARCHITECTURE.md` | Each project repo | Claude Code (on demand) | Architecture questions |
| `LAWS.md` | Each project repo | Claude Code (always loaded) | Every session |
| `CONTEXT.md` | Each project repo | Claude Code (always loaded) | Every session |
| `docs/INDEX.md` | Each project repo | Claude Code (always loaded, tiny) | Every session |

---

## The one-line version

Keel governs how work flows. lean-context governs what the agent sees.
Systems Thinking governs how you design. Install all three, keep them
separate, wire them together in `CLAUDE.md`. They don't overlap — they stack.
