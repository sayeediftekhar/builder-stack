# ARCHITECTURE.md — {{PROJECT_NAME}}

<!--
  The project-specific application of the seven-rung framework. Produced in
  your architect chat (load docs/SYSTEMS_THINKING_FRAMEWORK.md there first).
  Lives in docs/, referenced from the authorities index, fetched on demand.
-->

## Load-bearing pieces (built first, thin but correct)
Build these before any user-facing feature. Thinnest correct version only.
- [ ] Identity and tenancy model — {{WHO_IS_THE_USER_WHAT_CAN_THEY_SEE}}
- [ ] Core data model — {{THE_CORE_THINGS_AND_HOW_THEY_RELATE}}
- [ ] Money model (if applicable) — {{HOW_MONEY_IS_REPRESENTED_STORED_CALCULATED}}
- [ ] Core transaction — {{THE_ONE_THING_THE_SYSTEM_EXISTS_TO_DO}}

## Module map (one job per module)
| Module | Single job (one sentence, no "and also") | Stable or volatile? |
|--------|------------------------------------------|---------------------|
| {{MODULE}} | {{ONE_SENTENCE_JOB}} | {{STABLE_OR_VOLATILE}} |
| {{MODULE}} | {{ONE_SENTENCE_JOB}} | {{STABLE_OR_VOLATILE}} |
| {{MODULE}} | {{ONE_SENTENCE_JOB}} | {{STABLE_OR_VOLATILE}} |

## Iron Laws
The commit-blocking invariants live in **LAWS.md** — see it there, do not
duplicate. Summary of what they protect: {{ONE_LINE_ON_WHAT_THE_LAWS_GUARD}}

## Change surface decisions
- **Volatile (changes often):** {{LIST_VOLATILE_PIECES}}
- **Stable (foundation):** {{LIST_STABLE_PIECES}}
- **Separation mechanism:** {{HOW_VOLATILE_AND_STABLE_ARE_KEPT_APART}}

## Sequencing plan
- **Phase 0 — foundation:** {{THIN_CORRECT_LOAD_BEARING_PIECES}}
- **Slice 1:** {{FIRST_COMPLETE_VERTICAL_FEATURE_DB_TO_UI}}
- **Slice 2:** {{NEXT_SLICE_ORDERED_BY_DEPENDENCY_NOT_EXCITEMENT}}
- **Slice 3:** {{...}}

<!-- Each slice: database → logic → interface → UI, verified in the real
     environment before the next begins. -->
