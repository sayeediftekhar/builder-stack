# New Project Checklist — full stack install

Work top to bottom. Order matters: each step assumes the ones above it are
done. Commands are copy-pasteable as written.

- [ ] **Create the repo and initial commit**

- [ ] **Install Keel as submodule**
  ```bash
  git submodule add https://github.com/sayeediftekhar/Keel .claude/skills
  git submodule update --init --recursive
  ```

- [ ] **Add Keel routing line to CLAUDE.md** (copy from `templates/CLAUDE.md`)
  ```
  Route every task through keel-v2 before planning or writing code.
  ```

- [ ] **Fetch and run the lean-context directive**
  ```bash
  curl -O https://raw.githubusercontent.com/sayeediftekhar/lean-context/main/DIRECTIVE.md
  ```
  Then tell Claude Code:
  > Read DIRECTIVE.md and execute it. Stop at each STOP.

- [ ] **Archive DIRECTIVE.md after it runs** (it's a one-time setup tool)
  ```bash
  mkdir -p .archive && git mv DIRECTIVE.md .archive/DIRECTIVE.md
  ```

- [ ] **Run the architecture session**
  Open an architect chat (Claude.ai), load
  `docs/SYSTEMS_THINKING_FRAMEWORK.md`, and answer the seven-rung questions
  for this project.

- [ ] **Create `docs/ARCHITECTURE.md`** from `templates/ARCHITECTURE.md` using
  the architect output.

- [ ] **Create `LAWS.md`** from `templates/LAWS.md` — 4–8 project-specific
  invariants.

- [ ] **Create `context/core.md`** from `templates/CONTEXT_CORE.md`.

- [ ] **Create `docs/INDEX.md`** from `templates/docs_INDEX.md`.

- [ ] **Create `LEARNINGS.md`** from `templates/LEARNINGS.md`.

- [ ] **Finalise CLAUDE.md** — fill all placeholders, confirm ≤80 lines.

- [ ] **Start the first Claude Code session.** Verify:
  - Does it route through Keel?
  - Does it read `context/core.md` on session start?
  - Does it stay out of `docs/` without being asked?

- [ ] **Run Phase 0** (thin foundation) before any feature slices.
