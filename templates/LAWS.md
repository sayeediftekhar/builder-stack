# LAWS.md — {{PROJECT_NAME}} Iron Laws

<!--
  HOW TO DERIVE EACH LAW (from the quality-guarantees framework).
  A law earns a place here only if it is ALL THREE of:
    1. An invariant, not a preference — it must ALWAYS hold, no exceptions.
       "Prefer small functions" is a preference. "Every table row carries a
       tenant_id" is an invariant.
    2. Enforced in two layers — a structural mechanism (schema constraint,
       type, interface, folder boundary) AND a check (test, lint, CI gate,
       Keel gate). One layer alone is a rule that memory can bypass.
    3. Checkable per PR — you can point at a single PR and say yes/no, this
       law holds. If you cannot check it in one PR, it is a goal, not a law.
  Keep the list to 4–8. More than 8 means some are really preferences.
-->

1. **{{LAW_NAME}}:** {{LAW_DESCRIPTION}}
   - Structural enforcement: {{HOW_STRUCTURE_MAKES_IT_HARD_OR_IMPOSSIBLE}}
   - Per-PR check: {{HOW_YOU_VERIFY_IT_IN_ONE_PR}}

2. **{{LAW_NAME}}:** {{LAW_DESCRIPTION}}
   - Structural enforcement: {{HOW_STRUCTURE_MAKES_IT_HARD_OR_IMPOSSIBLE}}
   - Per-PR check: {{HOW_YOU_VERIFY_IT_IN_ONE_PR}}

3. **{{LAW_NAME}}:** {{LAW_DESCRIPTION}}
   - Structural enforcement: {{HOW_STRUCTURE_MAKES_IT_HARD_OR_IMPOSSIBLE}}
   - Per-PR check: {{HOW_YOU_VERIFY_IT_IN_ONE_PR}}

4. **{{LAW_NAME}}:** {{LAW_DESCRIPTION}}
   - Structural enforcement: {{HOW_STRUCTURE_MAKES_IT_HARD_OR_IMPOSSIBLE}}
   - Per-PR check: {{HOW_YOU_VERIFY_IT_IN_ONE_PR}}

<!-- Add laws 5–8 only if each passes all three tests above. Delete unused. -->
