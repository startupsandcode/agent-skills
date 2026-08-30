# UI Review PR Description Contract

## Summary

State the bounded UI correction and resulting user-visible behavior. Do not claim deployment or merge.

## Requirements authority

Record each authoritative source and exact reference, its approval status and relative authority, and the in-scope requirement IDs.

## Approved review report

Include or link the complete final report used for approval. Preserve its repository and UI target, traceability matrix, demonstrated gaps, out-of-scope observations, evidence handling, and uncertainty.

## Approved fix plan

Include or link the complete final plan used for approval. Preserve its gap mapping, intended behavior, affected files, ordered corrections, coverage, verification, evidence disposition, non-goals, and risks.

## Approval checkpoint

Record that the user directly approved both final artifacts in the current session and identify the approved artifact versions or content precisely enough to establish scope. Do not invent or paraphrase a quote, timestamp, approver identity, or approval evidence that was not observed.

## Actual changes

Map each changed file and behavior to an approved gap and plan step. Explain any implementation detail needed to understand the diff without expanding the approved scope.

## Final traceability results

Record the complete final matrix with exactly one disposition per requirement. Every approved gap must now be **Pass** with current rendered evidence; otherwise the workflow is **Blocked** and no PR may be created.

## Rendered evidence

For each visual or interaction claim, record the final environment or build identity, state, viewport, input, action, observed result, and current evidence reference. State the approved disposition of temporary screenshots or recordings and avoid sensitive data.

## Automated and repository verification

Record each exact command or repository-required action, result, and claim verified. Include tests, lint, type-check, build, complete diff review, worktree review, and staged-path review as applicable. A skipped, stale, incomplete, or failing relevant check blocks PR creation.

## Deviations

Record non-material implementation differences from the approved plan and their evidence. Write `None` when empty. This section cannot hide a material change; any material change requires updated artifacts and fresh approval before implementation continues.

## Residual risks

Record bounded risks that remain after complete verification, with mitigations or reviewer attention. Write `None` when empty. A relevant unknown or incomplete requirement is not a residual risk; it blocks PR creation.

## Remote verification

Before PR creation, complete and freeze every other section of this record; mark only the remote identity facts that cannot exist until creation as pending. After creation, fetch the PR and update only those newly known remote facts in this section. Do not change approved-artifact, implementation, traceability, evidence, verification, deviation, or risk content after creation. Refetch the PR from the remote service and record the repository, PR number and URL, base branch, head branch, head SHA, non-draft state, title, and complete description verification. A creation command is not evidence. Any mismatch or unavailable remote field makes the workflow **Blocked**; do not create a duplicate. Stop after the verified ready-for-review PR without deployment, merge, auto-merge, or merge queue entry.
