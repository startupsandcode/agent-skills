# UI Fix Plan Contract

## Gaps being corrected

List each demonstrated in-scope gap by stable requirement ID and link it to its review-report evidence. Every correction in this plan must map to one of these gaps. Exclude speculative cleanup and out-of-scope observations.

## Intended behavior

For each gap, state the exact observable result the approved correction will produce. Preserve the authoritative requirement; do not add redesign or unapproved behavior.

## Affected components and files

Name components, routes, and likely files using exact repository evidence. Explain why each path is expected to change and identify relevant existing tests and conventions. Do not treat likely paths as permission to modify unrelated files.

## Ordered corrections

Give the smallest coherent sequence of repository changes. Map every step to a gap and its intended behavior, including error handling and test-first work where applicable.

## States, viewports, and error paths

Enumerate the responsive states, viewports, inputs, identities, data conditions, interactions, loading or empty states, and error paths the correction must preserve or change.

## Automated regression coverage

Name exact tests to add or update, their repository paths, commands, setup, and expected claims. State how each assertion detects the demonstrated gap. If automation is not feasible, record the exact barrier and repeatable equivalent evidence.

## Rendered verification

For every corrected gap and affected requirement, specify the runtime environment, state, viewport, input, rendered action, evidence to inspect, and expected claim. The final run must repeat the complete traceability matrix and give every approved gap current rendered evidence as **Pass**.

## Dependencies and permissions

Record every dependency, integration, environment access, identity, secret, or permission needed and the repository evidence for it. For each non-applicable dependency or permission item, record `None` with reasoning.

## Migrations, rollout, and rollback

Record data or interface migrations, compatibility handling, release sequencing, rollout constraints, and rollback approach with supporting repository evidence. For every non-applicable migration, rollout, or rollback item, record `None` with reasoning. This workflow does not authorize deployment.

## Evidence disposition

List each temporary screenshot, recording, fixture, log, or other review artifact and its final disposition. Committing or externally storing previously temporary evidence is a material change unless the approved plan already permits it under repository convention. Avoid sensitive data.

## Verification commands and actions

List exact repository commands and rendered actions in execution order, including setup, focused automated checks, repository-required tests, lint, type-check, build, full diff review, worktree review, intended staging review, and final rendered inspection. Give the expected claim or result for every command and action.

## Risks, non-goals, and uncertainty

Record concrete implementation, regression, responsive, accessibility, security, privacy, and verification risks with mitigations. State explicit non-goals, including out-of-scope observations and speculative cleanup. List remaining uncertainty and the action that would resolve it.

## Material-change triggers

Fresh direct approval of an updated review report and fix plan is required if evidence materially changes any of: requirements authority or interpretation, gap scope, user-visible behavior, architecture, interfaces, dependencies, integrations, permissions, data handling, data model, migration, rollout, security, privacy, fix strategy, risk, or evidence retention.

## Approval-ready check

Confirm that every correction maps to a demonstrated in-scope gap; intended behavior matches authority; affected paths and ordered work use exact repository evidence; all relevant states, automated coverage, rendered checks, commands, dependencies, permissions, migrations, rollout, rollback, evidence disposition, risks, non-goals, and uncertainty are explicit; each non-applicable contract item says `None` with reasoning; and no speculative cleanup or out-of-scope observation is included. Present this complete final plan together with the complete final review report for direct approval.
