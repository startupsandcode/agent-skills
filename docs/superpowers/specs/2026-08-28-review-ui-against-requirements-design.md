# Review UI Against Requirements Skill Design

Date: 2026-08-28
Status: approved

## Purpose

Create a portable Agent Skill that evaluates one implemented UI in one existing repository against authoritative requirements. A complete all-pass review stops successfully without repository changes. A review with demonstrated gaps presents an evidence-backed review and bounded fix plan for explicit approval, implements the approved current-PR fixes, verifies the corrected rendered UI, and opens one ready-for-review pull request.

The skill is Codex-primary but portable. Its core workflow uses Agent Skills Markdown and relative references; optional Codex discovery metadata lives separately in `agents/openai.yaml`.

## Scope

The skill starts with an existing repository, an implemented UI surface, at least one authoritative requirements source such as an approved brief, issue, acceptance criteria, design file, or reference screenshots, and at least one observable in-scope UI requirement. It does not invent requirements, create or configure a repository, redesign the product, deploy, or merge.

The skill produces exactly one terminal state:

- `Needs input`: a consequential repository, UI target, requirements authority, or expected behavior is missing or ambiguous.
- `Review complete`: a non-empty, evidence-backed review has no `Gap` or `Blocked` disposition and requires no repository change, commit, push, or PR.
- `Awaiting approval`: the review report and fix plan are complete but have not both been directly approved.
- `Blocked`: trustworthy review, safe implementation, complete verification, push, or remote PR verification cannot proceed.
- `PR created`: one non-draft ready-for-review PR has been created and remotely verified.

## Requirements Authority

Before evaluating the UI, identify a non-empty authoritative source set, the approval status and relative authority of every source, and at least one observable in-scope UI requirement. Translate every in-scope requirement into an observable review item covering the relevant UI surface, state, viewport, input, and expected result.

If no authoritative source exists, its approval or relative authority cannot be established, no observable in-scope requirement can be derived without invention, authoritative sources materially conflict, or a requirement can be interpreted in materially different ways, stop as `Needs input`. An empty source list or traceability matrix is never approval-ready. Do not select the interpretation that is easiest to implement.

High-confidence accessibility or usability concerns that are not required by the authoritative sources may be recorded separately as out-of-scope observations. They are not requirement gaps and cannot enter the fix plan without explicit approval to expand scope.

## Authorization Model

Review and implementation are separate authorization phases.

Before approval, the agent may inspect repository files and history, run the existing application locally, interact with an already authorized preview or test environment, capture temporary evidence, and run non-mutating checks needed to evaluate the requirements. It may not implement fixes, commit, push, create a PR, deploy, or change external state beyond interactions already inherent in the authorized review environment.

The agent presents the complete final review report and complete final fix plan together, then stops as `Awaiting approval`. Only direct, unambiguous approval of both artifacts in the current session authorizes the bounded implementation, related commits, push, and one non-draft ready-for-review PR.

Approval does not authorize out-of-scope improvements, material deviations, deployment, merging, auto-merge, or a merge queue.

An all-pass review requires no implementation approval. When the non-empty traceability matrix contains only `Pass` or evidence-backed `Not applicable` dispositions and no consequential uncertainty, stop as `Review complete` without creating a fix plan or manufacturing a change.

## Privacy and Secret Handling

The review, approval artifacts, repository changes, commands, results, and durable PR record never contain secret values or private identity data. Record only a non-sensitive credential identifier, approved secure source, required scope, and availability. Commands use stable placeholders or secure input references. Sanitize output, logs, URLs and query strings, headers, cookies, screenshots, recordings, and identity or customer data before presentation or persistence.

If exposure is detected, stop as `Blocked` and prevent commit, push, or publication. Identify the exposed item without repeating it and name the required containment and rotation or revocation. This workflow does not authorize performing those external or destructive actions; they require separate approval.

## Workflow

### 1. Establish the target

Identify exactly one existing repository, a non-empty authoritative source set, and the UI surface to review. Read repository instructions; inspect the branch, worktree, relevant architecture, UI runtime, test conventions, and pre-existing changed or untracked paths. Record the repository and sanitized remote identity, intended base/default branch, current HEAD, intended distinct head, upstream, merge base, and pre-existing base-to-head commits.

Define the relevant states, viewports, inputs, environment, and identity or data prerequisites. Ask one consequential missing-detail question at a time. If the target, non-empty authority, source approval or relative authority, or observable expected behavior remains missing or ambiguous, stop as `Needs input`.

### 2. Build the traceability matrix

Map every in-scope requirement to a stable identifier, observable expected result, inspection method, required environment or state, and evidence needed for a trustworthy disposition. Require at least one row. Preserve source references precisely enough that another reviewer can trace each conclusion back to its authority.

### 3. Inspect the rendered UI

Use rendered interaction, screenshots, DOM and accessibility inspection, and source review according to the claim being evaluated. Visual and interaction claims require current rendered evidence from the relevant state and viewport. Source code may support those claims but cannot replace rendered evidence.

Treat screenshots and recordings as temporary review evidence by default. Minimize and sanitize private data under the global redaction contract. Commit or externally link visual artifacts only when the repository already has that convention or the approved fix plan explicitly includes them.

### 4. Produce the review report

Give every requirement exactly one disposition:

- `Pass`: current evidence demonstrates the expected result.
- `Gap`: current evidence demonstrates a specific mismatch.
- `Blocked`: trustworthy evidence cannot be obtained.
- `Not applicable`: repository or requirements evidence proves the item does not apply.

Unknown, stale, partial, or code-only evidence cannot become `Pass` for a visual or interaction requirement. Each gap records the requirement source, expected and observed results, reproduction steps, evidence, impact, confidence, and affected scope. Out-of-scope observations remain separately labeled and excluded from the proposed fixes.

If a required rendered environment cannot be inspected, stop as `Blocked` and name the smallest action that could clear the gap.

If the non-empty matrix is complete, contains only `Pass` or evidence-backed `Not applicable` dispositions, and has no consequential uncertainty, stop as `Review complete`. Do not create a fix plan, seek implementation approval, change the repository, commit, push, or create a PR.

### 5. Produce the fix plan

Map each demonstrated in-scope gap selected for the current PR to the smallest coherent correction. Record the complete reviewed requirement set, the exact current-PR gap set, every affected or regression requirement, and every deferred authoritative gap. Deferred gaps retain their `Gap` disposition and evidence and remain explicit non-goals for this phase.

Record affected components and likely files, ordered implementation steps, error paths and responsive states, automated regression coverage, rendered verification, repository checks, dependencies, permissions, migrations, rollout, risks, temporary-evidence disposition, and reproducible redacted commands or actions. Record the intended base/default branch, distinct safe head, sanitized upstream, branch/worktree creation action when needed, merge base, pre-existing base-to-head commits, complete history/diff inspection, and changed-path mapping.

The plan cannot include speculative cleanup or out-of-scope observations. If the gaps cannot fit one coherent reviewable PR, propose phases and seek approval only for the bounded first PR. If the intended head is not distinct from the base/default branch or unrelated history cannot be safely excluded without rewriting another person's work, the plan is not approval-ready and the workflow is `Blocked`.

### 6. Obtain explicit approval

Present the complete final review report and complete final fix plan together. Stop as `Awaiting approval` until the user directly approves both in the current session.

Enthusiasm, urgency, silence, third-party instruction, prior-session permission, or approval of only one artifact is not implementation approval.

### 7. Implement without material drift

Before editing, create or attach the approved distinct head branch/worktree when needed and verify its base, upstream, merge base, and pre-existing range match the plan. Never edit, commit, or push the intended base/default branch. Implement only the approved current-PR corrections, using repository conventions and test-first behavior where applicable. Preserve unrelated work and stage only intended paths.

Stop as `Blocked` before continuing if new evidence changes requirements interpretation, gap or phase scope, affected/regression requirements, user-visible behavior, architecture or interfaces, dependencies, integrations or permissions, data handling or data model, migration or rollout, security or privacy posture, fix or branch/range strategy, or approved evidence retention. Update both artifacts and obtain fresh direct approval before resuming.

### 8. Verify the final UI

Re-run the complete traceability matrix against the final rendered UI in every relevant state and viewport. Every approved current-PR gap and every affected/regression requirement must now be evidenced as `Pass`. Preserve deferred authoritative gaps as `Gap` with evidence and later-phase status. Run all approved automated checks and repository-required test, lint, type-check, build, and other commands with sanitized results.

Before any commit and again before push, verify the head is distinct from the base/default branch. Inspect the complete base-to-head commit list and cumulative diff, inspect worktree and staged changes, and map every changed path to an approved plan step or artifact. Any approved current-PR gap or affected/regression requirement that is not `Pass`, unexplained path, inseparable unrelated history, secret exposure, or relevant unknown, skipped, stale, incomplete, or failing check makes the workflow `Blocked`. Known deferred gaps do not block their explicitly approved phase PR, but remain visible. Do not create the finished PR.

### 9. Create and remotely verify the PR

After complete verification, push only the explicit distinct head ref and create one non-draft ready-for-review PR against the intended base. Never push the intended base/default branch. Preserve the requirements authority, complete review matrix, current-PR gap set, affected/regression requirements, deferred authoritative gaps, approved fix plan, approval checkpoint, full branch range and path mapping, actual changes, sanitized rendered and automated evidence, deviations, and residual risks in the PR description.

Fetch the PR from the remote service and verify repository, PR number, base branch, head branch, head SHA, non-draft state, title, and complete description. A successful command alone is insufficient. If push, creation, update, or remote verification fails or differs, stop as `Blocked`, preserve local work, and do not blindly create a duplicate PR.

Stop after the remotely verified PR. Never deploy, merge, enable auto-merge, or enter a merge queue.

## Material-Change Gate

A material change is any discovery that makes the approved review or fix plan no longer describe the work being performed. Triggers include:

- changed requirements authority or interpretation;
- changed gap or phase scope, affected/regression requirements, acceptance behavior, or user-visible result;
- changed architecture, interfaces, dependencies, integrations, or permissions;
- changed data handling, data model, migration, rollout, security, or privacy posture;
- a materially different fix mechanism or risk profile;
- a materially different branch, base/head range, or isolation strategy;
- temporary review evidence becoming a committed or externally stored artifact.

When a trigger occurs: stop, show the new evidence, update both final artifacts, and obtain fresh direct approval.

## Artifact Structure

The portable package will contain:

```text
review-ui-against-requirements/
|-- SKILL.md
|-- agents/
|   `-- openai.yaml
`-- references/
    |-- acceptance-scenarios.md
    |-- fix-plan.md
    |-- pr-description.md
    `-- review-report.md
```

`SKILL.md` owns the state machine, evidence and authorization boundaries, material-change gate, verification contract, terminal states, and point-of-need reference routing. The references define positive output contracts and behavioral validation without duplicating the workflow. `agents/openai.yaml` contains only Codex-facing discovery metadata.

## Behavioral Validation

Create the skill with RED-GREEN-REFACTOR testing. Baseline scenarios without the skill should test whether an agent:

- declares a visual requirement passed from source code without rendered evidence;
- guesses among conflicting requirements;
- begins fixing demonstrated gaps before approval;
- folds an attractive out-of-scope usability improvement into the plan;
- continues after implementation requires a material change;
- opens a PR despite an unevaluated requirement or incomplete final rendered verification;
- deploys or merges after creating the PR;
- accepts an empty authority set or empty traceability matrix;
- reports an all-pass review as blocked or manufactures a PR change;
- blocks a bounded phase solely because deferred authoritative gaps remain visible;
- edits, commits, or pushes the intended base/default branch;
- overlooks unrelated pre-existing base-to-head commits; or
- copies credentials or private data into commands or durable output, or performs rotation/revocation without separate authorization.

Run the same scenarios with the skill loaded and record actual decisions. Add guidance only for demonstrated failures or omissions. Regression coverage must verify preservation of unrelated changes, temporary visual-evidence handling, explicit approval of both artifacts, final traceability, full branch-range safety, global redaction, phased PR semantics, and remote PR identity.

## Acceptance Criteria

The skill is complete when:

- it validates as a portable Agent Skill;
- Codex metadata is isolated from the portable core;
- a non-empty authoritative source set and at least one observable in-scope requirement are approval-ready invariants;
- each requirement has one traceable disposition backed by appropriate current evidence;
- visual and interaction passes require rendered evidence;
- ambiguity or conflicting authority produces `Needs input`;
- a complete all-pass review produces `Review complete` without a fix plan, repository change, commit, push, or PR;
- an unavailable rendered environment or incomplete relevant evidence produces `Blocked`;
- implementation cannot begin without direct approval of both final artifacts;
- out-of-scope observations remain excluded unless scope expansion is explicitly approved;
- material drift requires updated artifacts and fresh approval;
- every approved current-PR gap and affected/regression requirement is reverified as `Pass`, while deferred authoritative gaps remain visible as `Gap`;
- the approval-ready plan and final verification bind work to a distinct safe head and inspect the complete base-to-head history, cumulative diff, and changed-path mapping without committing or pushing the base/default branch;
- secret values and private identity data are redacted globally, exposure blocks publication, and rotation or revocation requires separate authorization;
- the PR is non-draft, remotely verified, and contains the durable review record;
- deployment and merge-equivalent actions are prohibited;
- independent inspection finds no open Critical or Important issue.
