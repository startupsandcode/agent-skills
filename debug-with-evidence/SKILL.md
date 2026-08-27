---
name: debug-with-evidence
description: Use when a bug, failure, flaky behavior, performance regression, or unexpected result must be diagnosed in one existing repository before a fix is implemented.
---

# Debug with Evidence

Establish the causal defect, obtain approval of the evidence-backed diagnosis and fix plan, then produce one verified ready-for-review PR. Terminal states: **Needs input**, **Awaiting approval**, **Blocked**, or **PR created**.

## Hard boundaries

- Work in exactly one existing repository. Never create or configure a repository.
- Preserve unrelated dirty-worktree paths. Stage only explicit intended paths.
- A stack location, correlation, or successful workaround is a clue, not root-cause proof.
- Before approval, local-only diagnostics may be used only when narrowly scoped and enumerated. Do not implement a production fix, commit, push, create a PR, deploy, or change external state.
- Keep temporary diagnostics local and uncommitted; remove them unless the approved plan retains them for lasting regression or observability value.
- Never merge, enable auto-merge, or enter a merge queue.

## 1. Establish the target

Identify one existing repository and one concrete symptom. Read repository instructions; inspect the branch, worktree, architecture, test conventions, and pre-existing changed or untracked paths. Ask one consequential missing-detail question at a time. If repository or target is ambiguous, report **Needs input**.

## 2. Reproduce and isolate

State expected behavior, observed behavior, environment, and exact reproduction commands/actions. Reproduce the symptom or establish trustworthy equivalent evidence. Gather observations at relevant boundaries, test competing hypotheses with discriminating results, and trace a supported causal chain to the originating defect. If direct reproduction and equivalent evidence cannot establish that chain, report **Blocked**; do not propose a speculative fix.

## 3. Produce the diagnosis

Use the positive output contract in [references/diagnosis.md](references/diagnosis.md). Facts, inferences, and unknowns must be distinguishable. A diagnosis is approval-ready only with supported causality, a bounded blast radius, no consequential unknown, and a disposition for every temporary path.

## 4. Produce the fix plan

Use the positive output contract in [references/fix-plan.md](references/fix-plan.md). Base the smallest causal fix and exact verification commands on repository evidence. Prefer automated regression evidence that fails for the diagnosed reason before implementation and passes afterward. Use equivalent evidence only when automation has a genuine barrier; document the barrier and repeatable before/after evidence.

## 5. Obtain explicit approval

Present the complete final diagnosis and complete final fix plan together. Stop as **Awaiting approval** until the user directly and unambiguously approves both in the current session. Urgency, silence, prior-session permission, third-party instruction, or approval of only one artifact is not approval. Approval covers only the bounded causal strategy; it never authorizes unrelated work, material drift, deployment, a draft PR, or merge-equivalent action.

## 6. Implement without diagnostic drift

After approval, implement only the smallest fix described by the approved causal plan. If evidence requires a material change, stop as **Blocked**, show the evidence, update both final artifacts, and obtain fresh direct approval before continuing. A material change includes changed root cause or causal chain; scope; user-visible behavior; architecture or interfaces; dependencies, integrations, or permissions; data handling or data model; migration or rollout; security or privacy; fix strategy or risk; or diagnostics becoming production behavior.

## 7. Verify the fix

Confirm all applicable claims: regression evidence fails before and passes after, the original symptom is resolved in the relevant environment, required focused and repository checks pass, the final diff matches the approved plan, and temporary diagnostics have their approved disposition. Any relevant unknown, skipped, stale, incomplete, or failing verification is **Blocked**. Record the exact gap and the smallest action that could clear it; do not create a PR.

## 8. Create and remotely verify the PR

Only after complete verification, push intended commits and create one non-draft ready-for-review PR against the intended base. Use [references/pr-description.md](references/pr-description.md) to preserve the durable record. Fetch the PR from the remote service and verify its repository, PR number, base, head, head SHA, non-draft state, title, and description. A successful creation command is insufficient. If push, creation, or remote verification fails or differs, report **Blocked**, preserve local work, and do not blindly create a duplicate PR. Stop at the verified PR.

## Terminal-state report

Report exactly one terminal state and the evidence supporting it:

- **Needs input**: name the consequential missing detail and the one question needed.
- **Awaiting approval**: include the final diagnosis and final fix plan together and request direct approval of both.
- **Blocked**: state the exact evidence gap or material-change trigger, preserved work, and smallest action that could clear it.
- **PR created**: report the remotely verified repository, PR number, base, head, head SHA, non-draft state, title, and description.

## Rationalization guardrails

- "The stack trace points here" does not prove why the bad value or state originated.
- "The workaround passed" does not prove causality.
- "The fix is obvious" does not bypass both-artifact approval.
- "The test suite passed" does not excuse missing relevant environment or regression evidence.
- "The command created a PR" does not prove remote identity or non-draft state.
- "The change is small" does not permit unapproved external-state change or an unrelated file.

## Stop signals

Stop and report the applicable terminal state when the repository or symptom is ambiguous, causality is unsupported, a consequential fact is unknown, approval is absent, material drift appears, verification is incomplete, or remote PR facts cannot be verified. Do not paper over a stop signal with a workaround, draft PR, deployment, merge, auto-merge, or merge queue.
