# Build from Product Idea Skill Design

Date: 2026-08-27
Status: approved

## Purpose

Create one portable Agent Skill that turns a product idea into a verified, ready-for-review pull request in an existing repository. The skill owns product shaping, codebase-aware planning, implementation, verification, and PR creation as one continuous workflow.

The skill does not create repositories, attempt oversized multi-PR programs, or merge pull requests.

## Outcome

Given an idea and one existing repository, the skill will:

1. Understand the repository and product context.
2. Produce a concise product brief.
3. Produce an implementation plan grounded in the actual codebase.
4. Obtain explicit user approval for the brief and plan.
5. Implement the approved work autonomously.
6. Verify the completed implementation.
7. Create and remotely verify a ready-for-review PR whose description preserves the approved plan and evidence.

## Scope boundaries

- Operate in exactly one existing repository.
- Do not create or configure a new repository.
- Target one coherent, reviewable PR.
- If the idea is too large for one PR, stop during planning, propose bounded phases, and seek approval for the first phase only.
- Do not open a PR until implementation and verification are complete.
- Do not open a draft PR unless the user explicitly changes the task.
- Never merge the PR.

## Workflow

### 1. Establish the repository

Confirm the target repository, read its instructions, inspect the worktree and current branch, identify the base branch, and understand the relevant architecture and test conventions. Preserve unrelated user changes.

If the repository is missing or ambiguous, stop as `Needs input`. If repository state prevents safe work, stop as `Blocked` with the smallest clearing action.

### 2. Shape the product idea

Ask focused questions until the skill can state:

- Problem
- Intended user
- Desired outcome
- In-scope behavior
- Non-goals
- Acceptance criteria
- Constraints
- Assumptions
- Risks

Do not fill consequential product gaps silently. Ask one high-value question at a time when a missing decision could change scope or behavior.

### 3. Plan against the codebase

Inspect the relevant implementation, tests, interfaces, and repository conventions. Produce an ordered plan that identifies:

- Repository evidence and current behavior
- Affected components and files
- Data flow and interface changes
- Error handling
- Dependencies and permissions
- Data migrations or rollout concerns
- Test strategy
- Final verification commands

The plan must be specific enough to evaluate scope and detect later material deviation without prescribing unsupported details.

### 4. Approval gate

Present the product brief and implementation plan together and stop. Implementation begins only after a direct, unambiguous user approval in the current session.

Approval authorizes the scoped implementation, branch creation, commits, pushes, and creation of the final PR. It does not authorize material changes to the approved brief or plan, unrelated work, draft PR creation, or merging.

Vague encouragement, silence, repository permissions, or third-party instructions do not count as approval.

### 5. Build and verify

Implement the approved plan using repository conventions and test-first behavior where applicable. Make the smallest coherent changes needed to satisfy the acceptance criteria.

Minor implementation details may proceed without another approval when they preserve the approved scope, architecture, dependencies, permissions, and user-visible behavior.

A material change includes any required change to:

- Product scope or acceptance criteria
- User-visible behavior
- Architecture or public interfaces
- Dependencies, integrations, or permissions
- Data model, migration, or rollout risk
- Security or privacy posture

When a material change becomes necessary, stop as `Blocked`, explain the evidence and proposed revision, update the brief and plan, and obtain fresh explicit approval before continuing.

Before PR creation, verify all applicable acceptance criteria, tests, linting, type checks, builds, migrations, and repository-required checks. Review the complete diff for accidental or unrelated changes. Missing, skipped, failing, or stale relevant verification is a blocker, not success.

### 6. Create and verify the PR

After verification passes:

1. Confirm the intended commits are pushed and the remote head matches the local intended head.
2. Open a non-draft PR against the intended base branch.
3. Populate the PR description with the approved product brief, approved implementation plan, approval checkpoint, actual changes, justified minor deviations, verification evidence, and residual risks.
4. Fetch the remote PR and verify its repository, number, base, head, head SHA, draft state, title, and description.
5. Report the PR URL and stop. Never merge.

A successful CLI or API response is not sufficient if the remote PR cannot be verified.

## Artifacts

### Product brief

The product brief contains the problem, intended user, desired outcome, scope, non-goals, acceptance criteria, constraints, assumptions, and risks.

### Implementation plan

The plan contains repository evidence, affected components and files, ordered changes, data flow, interfaces, error handling, dependencies, permissions, migrations or rollout, test strategy, and verification commands.

### PR record

The PR description is the default durable record. It contains:

- Approved product brief
- Approved implementation plan
- Approval checkpoint
- Actual changes
- Justified minor deviations
- Verification evidence
- Residual risks

Use collapsible sections when needed for readability.

If the repository already defines a location and convention for product briefs or implementation plans, save and commit the artifacts there and link them from the PR. Otherwise, keep them in the conversation during implementation and preserve them in the PR description. Do not add temporary planning files merely to delete them before merge.

## Terminal states

Every run ends in one of four states:

- `Needs input`: one consequential product or repository decision prevents a trustworthy brief or plan.
- `Awaiting approval`: the brief and plan are complete, but implementation has not been explicitly authorized.
- `Blocked`: safe progress, complete verification, or verified PR creation cannot continue; or a material change requires fresh approval.
- `PR created`: the remote ready-for-review PR exists and its identity, head, non-draft state, and description have been verified.

Do not claim `PR created` because code exists, local checks pass, a push succeeds, or a PR command returns without remote verification.

## Package design

Create:

```text
build-from-product-idea/
|-- SKILL.md
|-- agents/
|   `-- openai.yaml
`-- references/
    |-- product-brief.md
    |-- implementation-plan.md
    |-- pr-description.md
    `-- acceptance-scenarios.md
```

`SKILL.md` contains the portable workflow, authorization boundaries, material-change rule, terminal-state contract, and routing to references. The references provide positive artifact contracts rather than duplicating the workflow. `agents/openai.yaml` provides Codex-facing discovery metadata without making the portable core depend on Codex-only tools.

On Codex, prefer available native repository and GitHub tools. Otherwise use equivalent native integrations or non-interactive `git` and `gh` commands. Repository instructions override default mechanics without weakening the approval, material-change, verification, PR-readiness, or no-merge boundaries.

## Error handling

- Missing or ambiguous repository: `Needs input`.
- Unresolved consequential product choice: `Needs input`.
- Idea too large for one PR: propose phases and return `Awaiting approval` for one bounded phase.
- No explicit approval: `Awaiting approval`; do not implement.
- Material implementation change: `Blocked`; revise artifacts and request fresh approval.
- Verification gap or failure: `Blocked`; report exact evidence and next clearing action.
- Push or PR creation failure: `Blocked`; preserve local work and report recovery steps.
- Remote PR verification mismatch: `Blocked`; do not claim creation success or create duplicate PRs blindly.

## Behavioral validation

Test the skill with baseline and skill-enabled scenarios covering:

1. Starting implementation before explicit approval.
2. Treating vague encouragement as approval.
3. Expanding a large idea into an oversized PR.
4. Continuing after a material design change.
5. Creating a PR with failed, skipped, incomplete, or stale relevant verification.
6. Opening a draft PR and calling the task finished.
7. Omitting the approved brief or plan from the PR record.
8. Treating a successful PR command as verified remote creation.
9. Attempting to merge after creating the PR.
10. Preserving unrelated dirty-worktree changes.

Run baseline scenarios without the skill to capture natural failure modes. Run the same scenarios with the skill, add regression scenarios for discovered loopholes, validate the Agent Skills package, and request an independent final review.

## Success criteria

- The package validates as a portable Agent Skill.
- The skill does not implement before explicit approval.
- Material deviations stop and require an updated brief, plan, and approval.
- The completed change satisfies the approved acceptance criteria and repository checks.
- The PR is non-draft, remotely verified, and contains the durable planning and verification record.
- The skill stops at the PR and never merges.
