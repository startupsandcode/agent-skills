# UI Fix Plan Contract

## Gaps being corrected

List each demonstrated in-scope gap selected for the current PR by stable requirement ID and link it to its review-report evidence. Every correction in this plan must map to one of these current-PR gaps. Exclude speculative cleanup and out-of-scope observations. If the complete review has no demonstrated gaps, do not create a plan; select **Review complete**.

## Review and current-PR scope

Record the complete reviewed requirement set, every demonstrated gap, the exact current-PR gap set, and every requirement that the current corrections can affect or must protect as regression coverage. List every deferred authoritative gap separately with its unchanged **Gap** disposition, evidence, reason for deferral, and intended later phase when known. The phase PR may not claim completion of the complete review or relabel, omit, or downgrade a deferred gap.

## Intended behavior

For each gap, state the exact observable result the approved correction will produce. Preserve the authoritative requirement; do not add redesign or unapproved behavior.

## Affected components and files

Name components, routes, and likely files using exact repository evidence. Explain why each path is expected to change and identify relevant existing tests and conventions. Do not treat likely paths as permission to modify unrelated files.

## Repository branch and PR range

Record the intended base/default branch and SHA, distinct safe head and SHA, sanitized upstream/remote identity, merge base, branch or worktree creation action when needed, and every pre-existing base-to-head commit. If a new head will be created only after approval, record its proposed name, creation point, expected merge base, and `None - new head` for the pre-existing range; require revalidation immediately after creation and before editing.

List the reproducible redacted commands or actions used to inspect the full base-to-head commit history and cumulative diff, plus worktree and index state. Map every existing changed path and commit to the approved plan or label it pre-existing and unrelated. The plan is not approval-ready if the head is the intended base/default branch or unrelated history cannot be separated without rewriting another person's work. No approved commit or push may target the base/default branch.

## Ordered corrections

Give the smallest coherent sequence of repository changes. Map every step to a gap and its intended behavior, including error handling and test-first work where applicable.

## States, viewports, and error paths

Enumerate the responsive states, viewports, inputs, identities, data conditions, interactions, loading or empty states, and error paths the correction must preserve or change.

## Automated regression coverage

Name exact tests to add or update, their repository paths, commands, setup, and expected claims. State how each assertion detects the demonstrated gap. If automation is not feasible, record the exact barrier and repeatable equivalent evidence.

## Rendered verification

For every current-PR gap and affected/regression requirement, specify the runtime environment, state, viewport, input, rendered action, evidence to inspect, and expected claim. The final run must repeat the complete traceability matrix, give every current-PR gap and affected/regression requirement current evidence as **Pass**, and preserve deferred authoritative gaps as **Gap**.

## Dependencies and permissions

Record every dependency, integration, environment access, identity, credential, or permission needed and the repository evidence for it. For a credential, record only its non-sensitive identifier, approved secure source, required scope, and availability - never its value, a fragment, a signed URL, session material, or identifying account data. For each non-applicable dependency or permission item, record `None` with reasoning.

## Migrations, rollout, and rollback

Record data or interface migrations, compatibility handling, release sequencing, rollout constraints, and rollback approach with supporting repository evidence. For every non-applicable migration, rollout, or rollback item, record `None` with reasoning. This workflow does not authorize deployment.

## Evidence disposition

List each temporary screenshot, recording, fixture, log, or other review artifact and its final disposition. Committing or externally storing previously temporary evidence is a material change unless the approved plan already permits it under repository convention. Sanitize artifacts, URLs, headers, cookies, identity data, and output before presentation or persistence. A detected exposure blocks commit, push, and publication; name any needed separately authorized rotation or revocation without performing it.

## Verification commands and actions

List reproducible repository commands and rendered actions in execution order, including safe-head creation or verification, setup, focused automated checks, repository-required tests, lint, type-check, build, full base-to-head commit and cumulative-diff review, worktree review, intended staging review, changed-path mapping, and final rendered inspection. Use stable placeholders or secure input references for credentials; never put secret values or private identity data in command arguments. Give a sanitized expected claim or result for every command and action and specify how output, logs, URLs, headers, cookies, screenshots, and identity data are redacted before capture.

## Risks, non-goals, and uncertainty

Record concrete implementation, branch/range isolation, regression, responsive, accessibility, security, privacy, and verification risks with mitigations. State explicit non-goals, including out-of-scope observations, speculative cleanup, and every deferred authoritative gap. List remaining uncertainty and the action that would resolve it.

## Material-change triggers

Fresh direct approval of an updated review report and fix plan is required if evidence materially changes any of: requirements authority or interpretation, gap or phase scope, affected or regression requirements, user-visible behavior, architecture, interfaces, dependencies, integrations, permissions, data handling, data model, migration, rollout, security, privacy, fix strategy, branch/range strategy, risk, or evidence retention.

## Approval-ready check

Confirm that every correction maps to a demonstrated current-PR gap; the complete review scope, exact current-PR gap set, affected/regression set, and deferred gap set are explicit; intended behavior matches authority; affected paths and ordered work use exact repository evidence; the intended head is distinct from the base/default branch; base, upstream, merge base, branch/worktree action, pre-existing commits, full history/diff inspection, and changed-path mapping are complete; and unrelated history is safely excluded. Confirm that all relevant states, automated coverage, rendered checks, redacted commands, sanitized results, dependencies, permissions, migrations, rollout, rollback, evidence disposition, risks, non-goals, and uncertainty are explicit; each non-applicable contract item says `None` with reasoning; no secret or private identity value is present; and no speculative cleanup or out-of-scope observation is included. Present this complete final plan together with the complete final review report for direct approval.
