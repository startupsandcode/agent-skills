# Fix-plan contract

Use this artifact with the final diagnosis for direct approval. Ground every change and command in repository evidence. Use `None - <reasoning>` for every non-applicable item.

## Root cause being corrected

- Fact: <root cause from final diagnosis>

## Intended behavior

- Fact: <observable behavior after the fix>

## Affected components and files

- Evidence: <repository evidence>
- Component/path: `<path>` - <bounded change>

## Causal fix

- Change: <smallest change that corrects the recorded causal chain>
- Why: <how it corrects the root cause rather than a symptom>

## Regression evidence

- Automated test: `<exact command>`
- Before implementation: <failure for the diagnosed reason>
- After implementation: <passing result>
- Equivalent evidence, if automation has a genuine barrier: <barrier, reasoning, and repeatable before/after commands/actions and results>

## Error paths and edge cases

- Case: <error path or edge case>
- Expected result: <result>

## Dependencies and permissions

- Dependencies: <None - reasoning, or exact dependency change and evidence>
- Permissions: <None - reasoning, or exact permission/integration effect and evidence>

## Migrations, rollout, and rollback

- Migrations: <None - reasoning, or exact migration>
- Rollout: <None - reasoning, or exact rollout>
- Rollback: <None - reasoning, or exact rollback>

## Verification commands

- `<exact command>` - <claim verified>

## Risks, non-goals, and uncertainty

- Risk/non-goal/uncertainty: <bounded statement and mitigation>

## Diagnostic disposition

- Path: `<temporary path>` - <remove, or retain with approved lasting regression/observability value>

## Material-change triggers

Stop as **Blocked**, update the final diagnosis and final fix plan, and obtain fresh direct approval if any of these changes: root cause or causal chain; scope; user-visible behavior; architecture or interfaces; dependencies, integrations, or permissions; data handling or data model; migration or rollout; security or privacy; fix strategy or risk; or diagnostics becoming production behavior.

## Approval-ready check

- Bounded causal fix supported by repository evidence: <Yes/No>
- Exact verification commands defined: <Yes/No>
- Regression evidence follows the automated rule or documents a genuine barrier and repeatable equivalent: <Yes/No>
- Dependencies, permissions, migrations, rollout, and rollback addressed separately: <Yes/No>
- Every temporary path has a disposition: <Yes/No>
- Result: <Approval-ready or Blocked>
