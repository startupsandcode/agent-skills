# Review UI Against Requirements Skill Design

Date: 2026-08-28
Status: approved

## Purpose

Create a portable Agent Skill that evaluates one implemented UI in one existing repository against authoritative requirements, presents an evidence-backed review and bounded fix plan for explicit approval, implements the approved fixes, verifies the corrected rendered UI, and opens one ready-for-review pull request.

The skill is Codex-primary but portable. Its core workflow uses Agent Skills Markdown and relative references; optional Codex discovery metadata lives separately in `agents/openai.yaml`.

## Scope

The skill starts with an existing repository, an implemented UI surface, and one or more authoritative requirements sources such as an approved brief, issue, acceptance criteria, design file, or reference screenshots. It does not invent requirements, create or configure a repository, redesign the product, deploy, or merge.

The skill produces exactly one terminal state:

- `Needs input`: a consequential repository, UI target, requirements authority, or expected behavior is missing or ambiguous.
- `Awaiting approval`: the review report and fix plan are complete but have not both been directly approved.
- `Blocked`: trustworthy review, safe implementation, complete verification, push, or remote PR verification cannot proceed.
- `PR created`: one non-draft ready-for-review PR has been created and remotely verified.

## Requirements Authority

Before evaluating the UI, identify the authoritative requirements sources and their relative authority. Translate every in-scope requirement into an observable review item covering the relevant UI surface, state, viewport, input, and expected result.

If authoritative sources materially conflict, or a requirement can be interpreted in materially different ways, stop as `Needs input`. Do not select the interpretation that is easiest to implement.

High-confidence accessibility or usability concerns that are not required by the authoritative sources may be recorded separately as out-of-scope observations. They are not requirement gaps and cannot enter the fix plan without explicit approval to expand scope.

## Authorization Model

Review and implementation are separate authorization phases.

Before approval, the agent may inspect repository files and history, run the existing application locally, interact with an already authorized preview or test environment, capture temporary evidence, and run non-mutating checks needed to evaluate the requirements. It may not implement fixes, commit, push, create a PR, deploy, or change external state beyond interactions already inherent in the authorized review environment.

The agent presents the complete final review report and complete final fix plan together, then stops as `Awaiting approval`. Only direct, unambiguous approval of both artifacts in the current session authorizes the bounded implementation, related commits, push, and one non-draft ready-for-review PR.

Approval does not authorize out-of-scope improvements, material deviations, deployment, merging, auto-merge, or a merge queue.

## Workflow

### 1. Establish the target

Identify exactly one existing repository, the authoritative requirements, and the UI surface to review. Read repository instructions; inspect the branch, worktree, relevant architecture, UI runtime, test conventions, and pre-existing changed or untracked paths.

Define the relevant states, viewports, inputs, environment, and identity or data prerequisites. Ask one consequential missing-detail question at a time. If the target or authority remains ambiguous, stop as `Needs input`.

### 2. Build the traceability matrix

Map every in-scope requirement to a stable identifier, observable expected result, inspection method, required environment or state, and evidence needed for a trustworthy disposition. Preserve source references precisely enough that another reviewer can trace each conclusion back to its authority.

### 3. Inspect the rendered UI

Use rendered interaction, screenshots, DOM and accessibility inspection, and source review according to the claim being evaluated. Visual and interaction claims require current rendered evidence from the relevant state and viewport. Source code may support those claims but cannot replace rendered evidence.

Treat screenshots and recordings as temporary review evidence by default. Avoid capturing sensitive data. Commit or externally link visual artifacts only when the repository already has that convention or the approved fix plan explicitly includes them.

### 4. Produce the review report

Give every requirement exactly one disposition:

- `Pass`: current evidence demonstrates the expected result.
- `Gap`: current evidence demonstrates a specific mismatch.
- `Blocked`: trustworthy evidence cannot be obtained.
- `Not applicable`: repository or requirements evidence proves the item does not apply.

Unknown, stale, partial, or code-only evidence cannot become `Pass` for a visual or interaction requirement. Each gap records the requirement source, expected and observed results, reproduction steps, evidence, impact, confidence, and affected scope. Out-of-scope observations remain separately labeled and excluded from the proposed fixes.

If a required rendered environment cannot be inspected, stop as `Blocked` and name the smallest action that could clear the gap.

### 5. Produce the fix plan

Map each demonstrated in-scope gap to the smallest coherent correction. Record affected components and likely files, ordered implementation steps, error paths and responsive states, automated regression coverage, rendered verification, repository checks, dependencies, permissions, migrations, rollout, risks, temporary-evidence disposition, and exact commands or actions.

The plan cannot include speculative cleanup or out-of-scope observations. If the gaps cannot fit one coherent reviewable PR, propose phases and seek approval only for the bounded first PR.

### 6. Obtain explicit approval

Present the complete final review report and complete final fix plan together. Stop as `Awaiting approval` until the user directly approves both in the current session.

Enthusiasm, urgency, silence, third-party instruction, prior-session permission, or approval of only one artifact is not implementation approval.

### 7. Implement without material drift

Implement only the approved corrections, using repository conventions and test-first behavior where applicable. Preserve unrelated work and stage only intended paths.

Stop as `Blocked` before continuing if new evidence changes requirements interpretation, gap scope, user-visible behavior, architecture or interfaces, dependencies, integrations or permissions, data handling or data model, migration or rollout, security or privacy posture, fix strategy, or approved evidence retention. Update both artifacts and obtain fresh direct approval before resuming.

### 8. Verify the final UI

Re-run the complete traceability matrix against the final rendered UI in every relevant state and viewport. Every approved gap must now be evidenced as `Pass`. Run all approved automated checks and repository-required test, lint, type-check, build, and other commands. Review the complete diff and intended staged paths.

Any in-scope requirement that remains `Gap` or `Blocked`, or any relevant unknown, skipped, stale, incomplete, or failing check, makes the workflow `Blocked`. Do not create the finished PR.

### 9. Create and remotely verify the PR

After complete verification, push the intended commits and create one non-draft ready-for-review PR against the intended base. Preserve the requirements authority, final traceability results, approved fix plan, approval checkpoint, actual changes, rendered and automated evidence, deviations, and residual risks in the PR description.

Fetch the PR from the remote service and verify repository, PR number, base branch, head branch, head SHA, non-draft state, title, and complete description. A successful command alone is insufficient. If push, creation, update, or remote verification fails or differs, stop as `Blocked`, preserve local work, and do not blindly create a duplicate PR.

Stop after the remotely verified PR. Never deploy, merge, enable auto-merge, or enter a merge queue.

## Material-Change Gate

A material change is any discovery that makes the approved review or fix plan no longer describe the work being performed. Triggers include:

- changed requirements authority or interpretation;
- changed gap scope, acceptance behavior, or user-visible result;
- changed architecture, interfaces, dependencies, integrations, or permissions;
- changed data handling, data model, migration, rollout, security, or privacy posture;
- a materially different fix mechanism or risk profile;
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
- deploys or merges after creating the PR.

Run the same scenarios with the skill loaded and record actual decisions. Add guidance only for demonstrated failures or omissions. Regression coverage must verify preservation of unrelated changes, temporary visual-evidence handling, explicit approval of both artifacts, final traceability, and remote PR identity.

## Acceptance Criteria

The skill is complete when:

- it validates as a portable Agent Skill;
- Codex metadata is isolated from the portable core;
- each requirement has one traceable disposition backed by appropriate current evidence;
- visual and interaction passes require rendered evidence;
- ambiguity or conflicting authority produces `Needs input`;
- an unavailable rendered environment or incomplete relevant evidence produces `Blocked`;
- implementation cannot begin without direct approval of both final artifacts;
- out-of-scope observations remain excluded unless scope expansion is explicitly approved;
- material drift requires updated artifacts and fresh approval;
- every approved gap is reverified as `Pass` in the final rendered UI;
- the PR is non-draft, remotely verified, and contains the durable review record;
- deployment and merge-equivalent actions are prohibited;
- independent inspection finds no open Critical or Important issue.
