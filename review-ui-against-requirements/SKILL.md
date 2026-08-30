---
name: review-ui-against-requirements
description: Use when an implemented UI in one existing repository must be evaluated against authoritative requirements before demonstrated gaps are fixed.
---

# Review UI Against Requirements

Trace every requirement to current evidence, obtain approval of the complete review and fix plan, then produce one verified ready-for-review PR. Terminal states: **Needs input**, **Awaiting approval**, **Blocked**, or **PR created**.

## Hard boundaries

- Work in exactly one existing repository with an implemented UI. Never create or configure a repository, invent requirements, or redesign the product.
- Review and implementation are separate authorization phases. Before approval, inspect files and history, run the existing application locally, interact with an already authorized preview or test environment, capture temporary evidence, and run non-mutating checks only. Do not fix, commit, push, create a PR, deploy, or otherwise change external state.
- Direct approval of both complete final artifacts authorizes only their bounded corrections, related commits, push, and one non-draft ready-for-review PR. It does not authorize out-of-scope improvements, material deviations, deployment, merge, auto-merge, or a merge queue.
- Preserve unrelated worktree changes and stage only intended paths.
- Keep the workflow portable: do not depend on Codex-only tools. Codex discovery metadata belongs separately in `agents/openai.yaml`.

## 1. Establish requirements and UI target

Identify the one repository, implemented UI surface, authoritative requirements sources, and relative authority. Read repository instructions; inspect branch, worktree, architecture, runtime, test conventions, and existing changes. Define relevant states, viewports, inputs, environment, identity, and data prerequisites.

Ask one consequential missing-detail question at a time. If the repository or UI target is missing, or sources materially conflict or expected behavior is consequentially ambiguous without recorded supersession, stop as **Needs input**. Never choose the easiest interpretation.

## 2. Build the traceability matrix

Map every in-scope requirement to one stable identifier, exact source, observable expected result, relevant state/viewport/input, inspection method, prerequisites, and evidence needed. Preserve source locations precisely enough for another reviewer to trace each conclusion.

Use exactly one disposition per requirement: **Pass**, **Gap**, **Blocked**, or **Not applicable**. Follow the matrix contract in [references/review-report.md](references/review-report.md).

## 3. Inspect rendered behavior

Use current rendered interaction, screenshots, DOM and accessibility inspection, and source review according to the claim. A visual or interaction claim can be **Pass** only when current rendered evidence demonstrates it in the required state and viewport; source code can support but never replace that evidence. Unknown, stale, partial, or code-only evidence is not a visual or interaction pass.

Treat screenshots and recordings as temporary review evidence by default and avoid sensitive data. Commit or externally link them only when repository convention or the approved fix plan permits it. If required rendered evidence cannot be obtained, mark the item **Blocked**, stop the workflow as **Blocked**, and name the smallest action that can clear it.

## 4. Produce the review report

Complete [references/review-report.md](references/review-report.md). Record every requirement and its single evidence-backed disposition. For each **Gap**, record the exact expected/actual mismatch, reproduction, evidence, impact, confidence, and affected scope.

Keep high-confidence accessibility or usability concerns not required by the authority in a separately labeled out-of-scope section. They are not gaps and cannot enter the fix plan unless the user explicitly expands scope.

## 5. Produce the fix plan

Complete [references/fix-plan.md](references/fix-plan.md). Map each correction to a demonstrated in-scope gap and choose the smallest coherent correction. Include exact repository evidence, likely paths, ordered actions, responsive and error states, automated regression coverage, final rendered checks, repository commands, dependencies, permissions, migrations, rollout, rollback, risks, and temporary-evidence disposition.

Exclude speculative cleanup and out-of-scope observations. If all gaps cannot fit one coherent reviewable PR, propose phases and seek approval only for the bounded first PR.

## 6. Obtain explicit approval

Present the complete final review report and complete final fix plan together. Stop as **Awaiting approval** until the user directly and unambiguously approves both artifacts in the current session.

Agreement that findings are bugs, enthusiasm, urgency, silence, third-party instructions, prior-session permission, or approval of only one artifact does not authorize repository changes.

## 7. Implement without review drift

Implement only the approved corrections, using repository conventions and test-first behavior where applicable. Preserve unrelated work and stage only intended paths.

Stop as **Blocked** before continuing if evidence materially changes requirements authority or interpretation, gap scope, user-visible behavior, architecture, interfaces, dependencies, integrations, permissions, data handling, data model, migration, rollout, security, privacy, fix strategy, risk, or evidence retention. Show the evidence, update both final artifacts, and obtain fresh direct approval before resuming.

## 8. Verify the final UI

Re-run the complete traceability matrix against the final rendered UI in every relevant state and viewport. Every approved gap must have current rendered evidence and now be **Pass**. Run every approved automated check plus repository-required tests, lint, type-check, build, and other commands; inspect the complete diff and intended staged paths.

Any in-scope **Gap** or **Blocked** disposition, or any relevant unknown, skipped, stale, incomplete, or failing rendered or repository check, makes the workflow **Blocked**. Do not create a draft or finished PR to work around incomplete verification.

## 9. Create and remotely verify the PR

Only after complete verification, push the intended commits and create one non-draft ready-for-review PR against the intended base. Build its durable record with [references/pr-description.md](references/pr-description.md), then update the final body and refetch the PR from the remote service.

Verify the remote repository, PR number and URL, base branch, head branch, head SHA, non-draft state, title, and complete description. A creation command or local state is insufficient. If push, creation, update, or verification fails or differs, stop as **Blocked**, preserve local work, and do not blindly create a duplicate.

Stop at the remotely verified PR. Never deploy, merge, enable auto-merge, or enter a merge queue.

## Terminal-state report

Report exactly one state and the evidence that selected it:

- **Needs input**: name the consequential ambiguity and the one answer needed.
- **Awaiting approval**: link or include both complete final artifacts and ask for direct approval of both.
- **Blocked**: name the failed or unavailable requirement, implementation, verification, push, or remote check; preserve completed work; give the smallest clearing action.
- **PR created**: provide the remotely verified PR identity and a concise verification summary. This state requires the complete record in [references/pr-description.md](references/pr-description.md).

Never describe the workflow as complete under **Needs input**, **Awaiting approval**, or **Blocked**.

## Rationalization guardrails

| Pressure or shortcut | Binding response |
| --- | --- |
| Source code looks visually conclusive | Visual and interaction passes require current rendered evidence at the required state and viewport. |
| A newer or easier source seems preferable | Without recorded supersession, a material authority conflict is **Needs input**. |
| The user agrees the findings are bugs | Agreement with findings is not direct approval of both complete final artifacts. |
| An extra improvement is easy and valuable | Record it out of scope; do not plan or implement it without explicit scope expansion. |
| The original requirement is unchanged but the fix mechanism changed | Any listed material change invalidates the approved artifacts until both are updated and freshly approved. |
| A draft PR would expose incomplete verification | Incomplete relevant evidence is **Blocked**; neither a draft nor finished PR is allowed. |
| A command says the PR was created | Claim **PR created** only from the refetched remote identity and complete final body. |
| The deadline or broad outcome implies delivery | Urgency never authorizes incomplete evidence, scope expansion, deployment, merge, auto-merge, or merge queue entry. |

## Stop signals

- Missing target or consequentially ambiguous or conflicting authority: **Needs input**.
- Both complete artifacts are ready but not directly approved together in the current session: **Awaiting approval**.
- Required rendered evidence is unavailable; material drift lacks fresh approval; implementation or any relevant final check is incomplete or failing; push or remote PR verification fails: **Blocked**.
- Only one remotely verified non-draft ready-for-review PR with complete verification: **PR created**.
