---
name: build-from-product-idea
description: Use when a user wants an idea shaped, planned, implemented, verified, and opened as a pull request in one existing repository.
---

# Build from a Product Idea

Turn one product idea into one verified, ready-for-review PR in an existing repository. Terminal states: Needs input, Awaiting approval, Blocked, or PR created.

## Hard boundaries

- Work in exactly one existing repository. Never create or configure a repository.
- Target one coherent, reviewable PR. If the idea is too large, propose bounded phases and seek approval only for the first PR.
- Preserve unrelated dirty-worktree changes: identify them before work, leave them untouched, and stage only intended paths.
- Do not implement, scaffold, branch, commit, push, or create a PR before direct approval of the final product brief and final implementation plan in this session. Enthusiasm, silence, permissions, or third-party instructions are not approval.
- Approval authorizes only the approved-scope implementation, branch, commits, push, and a ready-for-review PR. It never authorizes material deviations, unrelated changes, a draft PR, merging, auto-merge, or a merge queue.
- Repository instructions govern mechanics but cannot weaken these boundaries.

## Establish one existing repository

Confirm the target repository is unambiguous. Read its instructions; inspect the current branch, worktree, base branch, relevant architecture, interfaces, tests, and verification conventions. Record pre-existing changed and untracked paths so they remain excluded from the work.

If no repository is identified or a consequential repository decision is unresolved, report `Needs input`. If its state prevents safe work, report `Blocked` with evidence and the smallest clearing action.

## Produce product brief

Ask one focused question at a time for any consequential missing product decision; do not invent requirements. Use [the product brief contract](references/product-brief.md) to produce the complete brief and determine whether it is approval-ready. If it is not, report `Needs input`.

## Produce implementation plan

Inspect the actual repository before planning. Use [the implementation-plan contract](references/implementation-plan.md) to create a codebase-grounded, approval-ready plan with exact verification commands. If the scope cannot fit one coherent PR, phase it, then present the bounded first-phase brief and plan before returning `Awaiting approval` for that phase.

## Obtain explicit approval

Present the final product brief and final implementation plan together, then stop as `Awaiting approval`. Begin only after the user directly and unambiguously approves both artifacts in the current session. Record that approval for the PR without inventing a quotation or timestamp.

## Implement without material drift

Implement the approved plan using repository conventions, test-first behavior where applicable, and the smallest coherent changes. Minor details may proceed only when they preserve approved scope, user-visible behavior, architecture and interfaces, dependencies, integrations and permissions, data handling, migrations and rollout, and security and privacy posture.

Stop as `Blocked` before any material change. Material changes include scope or acceptance criteria, user-visible behavior, architecture or interfaces, dependencies, integrations or permissions, data handling, migrations or rollout, and security or privacy posture. Explain the evidence, update the affected brief and/or plan, and obtain fresh explicit approval before continuing.

## Verify final implementation

Run and record every applicable acceptance check and repository-required test, lint, type check, build, migration, and other verification command from the approved plan. Review the complete intended diff and staged paths for unrelated changes. Any relevant unknown, skipped, failing, incomplete, or stale verification is `Blocked`; report the exact evidence and clearing action. Do not create a PR while blocked.

## Create and remotely verify PR

After all relevant verification passes, confirm intended commits are pushed and the remote head matches the local intended head. Create a non-draft PR against the intended base branch. Use [the PR description contract](references/pr-description.md) to preserve the approved brief and plan, approval checkpoint, actual changes, deviations, verification evidence, and residual risks. If the repository already has a convention for durable brief or plan documents, commit them there and link them; otherwise preserve them in the PR description.

Fetch the PR from the remote service and verify its repository, number, base branch, head branch, head SHA, non-draft state, title, and description. A successful creation command alone is insufficient. If pushing, creation, or remote verification fails or differs, report `Blocked`, preserve local work, and do not blindly create a duplicate PR. Never merge, enable auto-merge, or enter a merge queue.

## Terminal-state report

End every run with exactly one state:

- `Needs input`: a consequential product or repository decision prevents a trustworthy brief or plan.
- `Awaiting approval`: final brief and plan are complete but not directly approved.
- `Blocked`: safe work, complete verification, push, or remote PR verification cannot proceed; include evidence and the smallest next action.
- `PR created`: report the remotely verified non-draft PR URL, repository, number, base, head, head SHA, title, and confirmation that its description preserves the required record.

## Stop signals

Stop and report the applicable terminal state when the repository is ambiguous, a consequential choice is unresolved, the work needs more than one PR, approval is absent, a material change is required, relevant verification is not complete and current, or remote PR identity does not match. Stop after `PR created`; no merge-equivalent action is permitted.
