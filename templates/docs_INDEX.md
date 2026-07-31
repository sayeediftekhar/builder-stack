# docs/INDEX.md — {{PROJECT_NAME}}

**Fetch on demand. Nothing here is preloaded.** This is the only eager import
in CLAUDE.md — a pointer table, not content. Read a file only when the current
task needs it.

| Topic | File |
|-------|------|
| Architecture, module map, sequencing | docs/ARCHITECTURE.md |
| Domain rules, business logic | {{DOMAIN_DOC_PATH}} |
| Database schema | {{SCHEMA_PATH}} |
| Iron Laws (commit-blocking) | LAWS.md |
| Living state / current phase | CONTEXT.md |
| Lessons learned | LEARNINGS.md |
| {{ADDED_TOPIC}} | {{ADDED_FILE_PATH}} |

<!-- Add a row whenever a new deep-reference doc is created. Keep this table
     short — if it grows past ~30 lines, the docs themselves are doing too
     much and need boundaries. -->
