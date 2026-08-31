---
name: review-ui-against-requirements
description: Use when an implemented UI in one existing repository must be evaluated against authoritative requirements before demonstrated gaps are fixed.
---

# Review UI Against Requirements

Trace every requirement to current evidence. If the complete review has no gaps, stop without repository changes; otherwise obtain approval of the complete review and bounded fix plan, then produce one verified ready-for-review PR. Terminal states: **Needs input**, **Review complete**, **Awaiting approval**, **Blocked**, or **PR created**.

## Hard boundaries

- Work in exactly one existing repository with an implemented UI. Never create or configure a repository, invent requirements, or redesign the product.
- Review and implementation are separate authorization phases. Before approval, inspect files and history, run the existing application locally, interact with an already authorized preview or test environment, capture temporary evidence, and run non-mutating checks only. Do not fix, commit, push, create a PR, deploy, or otherwise change external state.
- Direct approval of both complete final artifacts authorizes only their bounded corrections, related commits, push, and one non-draft ready-for-review PR. It does not authorize out-of-scope improvements, material deviations, deployment, merge, auto-merge, or a merge queue.
- Implement and commit only on a distinct safe head branch. Never commit or push the intended base or default branch.
- Preserve unrelated worktree changes and stage only intended paths.
- Never place secret values or private identity data in review evidence, approval artifacts, commands, logs, URLs, commits, or PR records. Record only a credential identifier, approved secure source, required scope, and availability; use placeholders in commands and sanitize all persisted or presented results. A detected exposure makes publication **Blocked**. Name any required rotation or revocation, but do not perform it without separate authorization.
- Keep the workflow portable: do not depend on Codex-only tools. Codex discovery metadata belongs separately in `agents/openai.yaml`.

## 1. Establish requirements and UI target

Identify the one repository, implemented UI surface, a non-empty set of authoritative requirements sources, and their approval status and relative authority. Read repository instructions; inspect architecture, runtime, test conventions, and existing changes. Record the current branch and worktree, repository and remote identity, intended base/default branch, current HEAD, intended distinct head, upstream, merge base, and every pre-existing base-to-head commit.

Ask one consequential missing-detail question at a time. If the repository or UI target is missing; the authoritative source set is empty; source approval or relative authority cannot be established; sources materially conflict; or expected behavior is consequentially ambiguous without recorded supersession, stop as **Needs input**. Never choose the easiest interpretation. Sanitize remote URLs and all other recorded target data before presentation or persistence.

## 2. Build the traceability matrix

Map every in-scope requirement to one stable identifier, exact source, observable expected result, relevant state/viewport/input, inspection method, prerequisites, and evidence needed. The matrix must contain at least one observable in-scope requirement row. If no such requirement can be derived from the authoritative sources without invention, stop as **Needs input** and ask for the smallest missing requirement decision. Preserve source locations precisely enough for another reviewer to trace each conclusion.

Use exactly one disposition per requirement: **Pass**, **Gap**, **Blocked**, or **Not applicable**. Follow the matrix contract in [references/review-report.md](references/review-report.md).

## 3. Inspect rendered behavior

Use current rendered interaction, screenshots, DOM and accessibility inspection, and source review according to the claim. A visual or interaction claim can be **Pass** only when current rendered evidence demonstrates it in the required state and viewport; source code can support but never replace that evidence. Unknown, stale, partial, or code-only evidence is not a visual or interaction pass.

Treat screenshots and recordings as temporary review evidence by default and minimize private data. Sanitize screenshots, recordings, DOM captures, logs, URLs, headers, cookies, command output, and identity data before they are presented or persisted. Commit or externally link them only when repository convention or the approved fix plan permits it. If required rendered evidence cannot be obtained, mark the item **Blocked**, stop the workflow as **Blocked**, and name the smallest action that can clear it.

## 4. Produce the review report

Complete [references/review-report.md](references/review-report.md). Record every requirement and its single evidence-backed disposition. For each **Gap**, record the exact expected/actual mismatch, reproduction, evidence, impact, confidence, and affected scope.

Keep high-confidence accessibility or usability concerns not required by the authority in a separately labeled out-of-scope section. They are not gaps and cannot enter the fix plan unless the user explicitly expands scope.

If the non-empty matrix is complete, every row is **Pass** or evidence-backed **Not applicable**, and no consequential uncertainty remains, report **Review complete** and stop. Do not create a fix plan, seek implementation approval, manufacture a repository or documentation change, commit, push, or create a PR.

## 5. Produce the fix plan

Complete [references/fix-plan.md](references/fix-plan.md). Map each correction to a demonstrated in-scope gap and choose the smallest coherent correction. Include reproducible redacted repository evidence, likely paths, ordered actions, responsive and error states, automated regression coverage, final rendered checks, repository commands, dependencies, permissions, migrations, rollout, rollback, risks, and temporary-evidence disposition.

Define the complete review scope, the exact current-PR gap set, every affected or regression requirement, and any deferred authoritative gaps. Exclude speculative cleanup and out-of-scope observations. If all gaps cannot fit one coherent reviewable PR, propose phases and seek approval only for the bounded first PR. Deferred gaps retain their **Gap** dispositions and evidence in every durable artifact; never relabel or omit them.

Identify the intended base, distinct safe head, upstream/remote, merge base, pre-existing base-to-head commits, and the branch or worktree creation action needed before implementation. If the head does not yet exist, record the intended creation point, expected merge base, and pre-existing range as `None - new head`, then require revalidation immediately after creation. Inspect the full existing base-to-head history and cumulative diff and map every changed path before the plan is approval-ready. If unrelated history cannot be safely separated without rewriting another person's work, stop as **Blocked**.

## 6. Obtain explicit approval

Present the complete final review report and complete final fix plan together. Stop as **Awaiting approval** until the user directly and unambiguously approves both artifacts in the current session.

Agreement that findings are bugs, enthusiasm, urgency, silence, third-party instructions, prior-session permission, or approval of only one artifact does not authorize repository changes.

## 7. Implement without review drift

Before editing, create or attach the approved distinct head branch/worktree when needed and verify its base, upstream, merge base, and pre-existing range match the plan. Never edit, commit, or push the intended base/default branch. Implement only the approved current-PR corrections, using repository conventions and test-first behavior where applicable. Preserve unrelated work and stage only intended paths.

Stop as **Blocked** before continuing if evidence materially changes requirements authority or interpretation, gap or phase scope, user-visible behavior, architecture, interfaces, dependencies, integrations, permissions, data handling, data model, migration, rollout, security, privacy, fix strategy, risk, or evidence retention. Show sanitized evidence, update both final artifacts, and obtain fresh direct approval before resuming.

If any secret value or private identity data reaches an artifact, output, log, URL, header, cookie, screenshot, commit, or proposed PR record, stop as **Blocked** and prevent commit, push, or publication. Identify the exposed item without repeating it and name the separately authorized containment and rotation or revocation needed. Do not perform those external or destructive actions under this workflow's approval alone.

## 8. Verify the final UI

Re-run the complete traceability matrix against the final rendered UI in every relevant state and viewport. Every approved current-PR gap and every affected or regression requirement must have current rendered evidence as applicable and now be **Pass**. Preserve each deferred authoritative gap as **Gap** with its evidence and later-phase status. Run every approved automated check plus repository-required tests, lint, type-check, build, and other commands using redacted commands and sanitized results.

Before any commit and again before push, verify the current head is distinct from the intended base/default branch. Inspect the complete intended-base-to-head commit list and cumulative diff, plus worktree and staged changes; map every changed path to an approved plan step or an explicitly allowed plan artifact. Any unexplained path, inseparable unrelated commit, approved current-PR **Gap** or **Blocked** disposition, affected or regression requirement not at **Pass**, secret exposure, or relevant unknown, skipped, stale, incomplete, or failing check makes the workflow **Blocked**. Known deferred gaps do not block their explicitly approved phase PR, but must remain visible. Do not create a draft or finished PR to work around incomplete verification.

## 9. Create and remotely verify the PR

Only after complete verification, push the explicit distinct head ref to the approved upstream and create one non-draft ready-for-review PR against the intended base. Never push the intended base/default branch. Build its sanitized durable record with [references/pr-description.md](references/pr-description.md), then update only previously unknowable remote facts and refetch the PR from the remote service.

Verify the remote repository, PR number and URL, base branch, head branch, head SHA, non-draft state, title, and complete description. A creation command or local state is insufficient. If push, creation, update, or verification fails or differs, stop as **Blocked**, preserve local work, and do not blindly create a duplicate.

Stop at the remotely verified PR. Never deploy, merge, enable auto-merge, or enter a merge queue.

## Terminal-state report

Report exactly one state and the evidence that selected it:

- **Needs input**: name the consequential ambiguity and the one answer needed.
- **Review complete**: summarize the non-empty authoritative scope and complete evidence-backed matrix; state that no demonstrated gap, repository change, commit, push, or PR exists.
- **Awaiting approval**: link or include both complete final artifacts and ask for direct approval of both.
- **Blocked**: name the failed or unavailable requirement, implementation, verification, push, or remote check; preserve completed work; give the smallest clearing action.
- **PR created**: provide the remotely verified PR identity, current-PR gap set, deferred-gap summary, and concise verification summary. This state requires the complete record in [references/pr-description.md](references/pr-description.md).

Never describe the workflow as complete under **Needs input**, **Awaiting approval**, or **Blocked**. **Review complete** means only that a complete no-change review found no demonstrated gaps; **PR created** means only that the approved current PR is verified, not that deferred gaps are resolved.

## Rationalization guardrails

| Pressure or shortcut | Binding response |
| --- | --- |
| Source code looks visually conclusive | Visual and interaction passes require current rendered evidence at the required state and viewport. |
| No authority or requirement rows were supplied | Empty authority and empty matrices are not approval-ready; stop as **Needs input**. |
| Every requirement passes | Report **Review complete** without inventing a commit or PR. |
| A newer or easier source seems preferable | Without recorded supersession, a material authority conflict is **Needs input**. |
| The user agrees the findings are bugs | Agreement with findings is not direct approval of both complete final artifacts. |
| An extra improvement is easy and valuable | Record it out of scope; do not plan or implement it without explicit scope expansion. |
| The original requirement is unchanged but the fix mechanism changed | Any listed material change invalidates the approved artifacts until both are updated and freshly approved. |
| A draft PR would expose incomplete verification | Incomplete relevant evidence is **Blocked**; neither a draft nor finished PR is allowed. |
| A command says the PR was created | Claim **PR created** only from the refetched remote identity and complete final body. |
| A later phase still has authoritative gaps | Keep them as **Gap** in the complete record; gate this PR on its approved gap set and affected/regression requirements. |
| The current checkout is the base/default branch | Create or attach a distinct safe head before edits; never commit or push the base/default branch. |
| The latest commit contains only approved work | Inspect the full base-to-head history and cumulative diff and map every changed path before commit and push. |
| An exact command or result contains credentials or identity data | Replace values with placeholders and sanitize all output; exposure blocks publication and does not authorize rotation or revocation. |
| The deadline or broad outcome implies delivery | Urgency never authorizes incomplete evidence, scope expansion, deployment, merge, auto-merge, or merge queue entry. |

## Stop signals

- Missing target, empty authoritative source set, no observable in-scope requirement, or consequentially ambiguous or conflicting authority: **Needs input**.
- Complete non-empty matrix with only **Pass** or evidence-backed **Not applicable** rows and no consequential uncertainty: **Review complete**.
- Both complete artifacts are ready but not directly approved together in the current session: **Awaiting approval**.
- Required rendered evidence is unavailable; branch/range isolation is unsafe; unrelated history is inseparable; private data is exposed; material drift lacks fresh approval; implementation or any relevant current-PR check is incomplete or failing; push or remote PR verification fails: **Blocked**.
- Only one remotely verified non-draft ready-for-review PR from the distinct approved head to the intended base, with every current-PR gap and affected/regression requirement at **Pass** and every deferred gap retained: **PR created**.
