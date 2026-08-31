# UI Review PR Description Contract

## Summary

State the bounded current-PR UI correction and resulting user-visible behavior. Name the current-PR gap set. If authoritative gaps are deferred, state plainly that this phase does not complete the full review. Do not claim deployment or merge.

## Requirements authority

Record each authoritative source and exact reference, its approval status and relative authority, the complete reviewed requirement set, the exact current-PR gap set, every affected/regression requirement, and every deferred authoritative gap.

## Approved review report

Embed the complete final report used for approval in the PR body by default. Preserve its repository and UI target, traceability matrix, demonstrated gaps, out-of-scope observations, evidence handling, and uncertainty. A link is allowed only when it identifies an immutable or version-pinned artifact that is durably available to every intended reviewer. Record the artifact's stable identity and version, then verify its remote accessibility and content identity before claiming **PR created**. Reject local filesystem paths, session-only locations, mutable unversioned links, inaccessible artifacts, or links whose fetched content cannot be matched to the approved report.

## Approved fix plan

Embed the complete final plan used for approval in the PR body by default. Preserve its complete-review/current-PR/deferred scope, gap mapping, intended behavior, affected files, branch and PR range, ordered corrections, coverage, verification, evidence disposition, non-goals, and risks. A link is allowed only under the same immutable or version-pinned, durably reviewer-accessible contract as the approved report: record the stable identity and version, verify remote accessibility and content identity before claiming **PR created**, and reject local, session-only, mutable, inaccessible, or content-mismatched references.

## Approval checkpoint

Record that the user directly approved both final artifacts in the current session and identify the approved artifact versions or content precisely enough to establish scope. Do not invent or paraphrase a quote, timestamp, approver identity, or approval evidence that was not observed.

## Actual changes

Record the intended base, distinct head, sanitized upstream identity, merge base, and complete base-to-head commit range. Map every changed file and behavior in the cumulative PR diff to an approved current-PR gap and plan step or to an explicitly approved plan artifact. Explain any implementation detail needed to understand the diff without expanding the approved scope. No commit or push may target the intended base/default branch.

## Final traceability results

Record the complete final matrix with exactly one disposition per requirement. Every approved current-PR gap and every affected/regression requirement must now be **Pass** with current evidence; otherwise the workflow is **Blocked** and no PR may be created. Preserve each deferred authoritative gap as **Gap** with its evidence and later-phase status.

## Deferred authoritative gaps

List each gap excluded from this approved phase with its stable requirement ID, unchanged **Gap** disposition, evidence, reason for deferral, and intended later phase when known. Use `None` only when the complete review has no deferred gap. Never relabel deferred gaps as observations, residual risks, or resolved work.

## Rendered evidence

For each visual or interaction claim, record the final environment or build identity, state, viewport, input, action, observed result, and current evidence reference. State the approved disposition of temporary screenshots or recordings. Sanitize screenshots, logs, URLs, headers, cookies, command output, and identity or customer data before presentation or persistence.

## Automated and repository verification

Record each reproducible redacted command or repository-required action, sanitized result, and claim verified. Commands use placeholders or approved secure references for credentials and never contain secret values. Include tests, lint, type-check, build, current-head/base verification, the complete base-to-head commit list and cumulative diff, exhaustive changed-path mapping, worktree review, and staged-path review. A base/default-branch head, unrelated or unexplained history, exposed secret or private data, or skipped, stale, incomplete, or failing relevant current-PR check blocks PR creation.

## Deviations

Record non-material implementation differences from the approved plan and their evidence. Write `None` when empty. This section cannot hide a material change; any material change requires updated artifacts and fresh approval before implementation continues.

## Residual risks

Record bounded risks that remain after complete current-PR verification, with mitigations or reviewer attention. Write `None` when empty. A relevant unknown or incomplete current-PR requirement is not a residual risk; it blocks PR creation. Deferred authoritative gaps belong in their dedicated section and remain **Gap**.

## Remote verification

Before PR creation, complete and freeze every other section of this sanitized record; mark only the remote identity facts that cannot exist until creation as pending. After creation, fetch the PR and update only those newly known remote facts in this section. Do not change approved-artifact, implementation, traceability, deferred-gap, evidence, verification, deviation, or risk content after creation. Refetch the PR from the remote service and record the repository, PR number and URL, base branch, head branch, head SHA, non-draft state, title, and complete description verification. When an approved artifact uses the narrowly permitted link exception, also fetch it remotely as an intended reviewer and verify its stable identity, recorded version, accessibility, and content match the approved artifact. A creation command or body text containing a link is not evidence. Any mismatch, inaccessible artifact, mutable or unversioned link, unavailable remote field, or secret/private-data exposure makes the workflow **Blocked**; do not create a duplicate or publish the contaminated record. Identify exposed data without repeating it and name separately authorized rotation or revocation; do not perform it under this workflow's approval. Stop after the verified ready-for-review PR without deployment, merge, auto-merge, or merge queue entry.
