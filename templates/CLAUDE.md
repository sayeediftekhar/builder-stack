# {{PROJECT_NAME}} — Agent Instructions

<!--
  Fill every {{PLACEHOLDER}}. Keep this file ≤80 lines total.
  This is Tier 1 — the only always-loaded prose. Everything deep lives in
  docs/ and is fetched on demand via the authorities index below.
-->

## Truth order
live DB/schema/data > code > prose docs. On conflict, the live source wins.

## Operating model
- Route every task through keel-v2 before planning or writing code.
- One task = one PR = one context boundary.
- Plan before code. Verify in the real environment. Green tests are not proof.
- Load context on demand. Never front-load docs/.

## Iron Laws
{{LIST_4_TO_8_LAWS}}
<!-- The commit-blocking invariants for this project. Full text in LAWS.md;
     list them here by name/number so they are always in view. -->

## Session start
Read context/core.md. Check git status. Read the task spec. Do NOT preload docs/.

## Authorities index
| Topic | File | What it governs |
|-------|------|----------------|
| Architecture, module map, sequencing | docs/ARCHITECTURE.md | Structure decisions |
| Domain rules, business logic | {{DOMAIN_DOC_PATH}} | What the system does |
| Database schema | {{SCHEMA_PATH}} | Source of truth for all data shapes |
| Iron Laws (commit-blocking) | LAWS.md | Non-negotiable invariants |
| Living state / current phase | context/core.md | Where we are right now |
| Lessons learned | LEARNINGS.md | Trap → rule → why |
| On-demand index | docs/INDEX.md | Pointer table for everything else |

@docs/INDEX.md
