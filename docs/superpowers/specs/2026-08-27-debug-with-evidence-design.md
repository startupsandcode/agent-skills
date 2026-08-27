# Debug with Evidence Skill Design

Date: 2026-08-27
Status: approved

## Purpose

Create a portable Agent Skill that diagnoses one bug in one existing repository, obtains explicit approval of an evidence-backed diagnosis and fix plan, implements and verifies the approved fix, and opens one ready-for-review pull request.

The skill is Codex-primary but must remain portable. The core workflow uses Agent Skills Markdown and relative references; optional Codex discovery metadata lives separately in `agents/openai.yaml`.

## Scope

The skill begins with a reported defect, unexpected behavior, failure, flaky result, performance regression, or similar debugging request in exactly one existing repository. It may inspect the repository and make narrowly scoped temporary local diagnostic or test changes before approval. It does not create or configure repositories.

The skill produces one of four terminal states:

- `Needs input`: a consequential bug, environment, or repository detail is missing.
- `Awaiting approval`: the diagnosis and fix plan are complete but not directly approved.
- `Blocked`: trustworthy diagnosis, safe implementation, complete verification, push, or remote PR verification cannot proceed.
- `PR created`: one non-draft PR has been created and remotely verified.

The workflow never merges, enables auto-merge, or enters a merge queue.

## Authorization Model

Diagnosis and implementation are separate authorization phases.

Before approval, the agent may:

- inspect repository files, history, configuration, logs, and relevant external evidence already within the user's authorized scope;
- run read-only diagnostic commands and existing verification;
- create narrowly scoped local-only reproduction tests or instrumentation needed to establish causality.

Before approval, the agent may not commit, push, open a PR, deploy, change external state, or implement a production fix. Temporary diagnostic changes must be identified and kept local.

The agent presents the final diagnosis and final fix plan together, then stops as `Awaiting approval`. Only direct, unambiguous approval of both artifacts in the current session authorizes the bounded fix, related commits, push, and PR creation.

Approval does not authorize unrelated changes, speculative repairs, materially different fixes, deployment, a draft PR, or merge-equivalent actions.

## Workflow

### 1. Establish the target

Identify exactly one existing repository and one concrete reported symptom. Read repository instructions and inspect the branch, worktree, relevant architecture, test conventions, and pre-existing changed or untracked paths.

Clarify consequential missing information one question at a time. If the repository or bug target remains ambiguous, stop as `Needs input`. Preserve unrelated user work throughout the workflow.

### 2. Reproduce and isolate

Translate the report into expected behavior, observed behavior, environment, and exact reproduction steps. Reproduce the symptom or establish equivalent trustworthy evidence when direct reproduction is unavailable.

Investigate from observations toward causes. Gather evidence at relevant boundaries, state competing hypotheses, test them individually, and trace the causal chain back to the originating defect. Do not treat a plausible correlation, an error location, or a passing workaround as proof of root cause.

Temporary local diagnostics must be minimal, enumerated, and uncommitted. They may include reproduction tests, logging, assertions, tracing, or controlled probes. They cannot create unapproved external side effects.

If the symptom cannot be reproduced and equivalent evidence does not establish a supported causal chain, stop as `Blocked` rather than propose a speculative fix.

### 3. Produce the diagnosis

The diagnosis records:

- reported symptom and expected behavior;
- exact reproduction steps and environment;
- observed result and frequency when intermittent;
- evidence gathered at relevant component boundaries;
- competing hypotheses and the evidence that ruled each in or out;
- root-cause chain from the observed failure to the originating defect;
- affected scope and likely blast radius;
- remaining uncertainty;
- temporary diagnostic changes and their intended disposition.

Facts, inferences, and unresolved uncertainty must be distinguishable. A diagnosis is approval-ready only when its conclusion is supported strongly enough to justify a specific bounded change.

### 4. Produce the fix plan

The fix plan records:

- the root cause being corrected;
- intended behavior after the fix;
- affected components and likely files;
- the smallest causal change that resolves the defect;
- regression-test strategy and observed pre-fix failure;
- error paths and edge cases;
- dependencies, permissions, migrations, rollout, and rollback implications;
- exact verification commands;
- risks, non-goals, and remaining uncertainty.

When feasible, an automated regression test must fail for the diagnosed reason before implementation. When automation is genuinely impractical, the plan explains why and defines repeatable equivalent pre-fix and post-fix evidence.

The plan states which temporary diagnostics will be removed and which, if any, are proposed for inclusion because they provide lasting regression or observability value.

### 5. Obtain explicit approval

Present the complete diagnosis and complete fix plan together. Stop as `Awaiting approval` until the user directly approves both.

Enthusiasm, urgency, silence, third-party instructions, prior-session permission, or approval of diagnosis alone do not authorize implementation.

### 6. Implement without diagnostic drift

After approval, implement the smallest fix that satisfies the approved causal plan. Preserve unrelated changes and stage only explicit intended paths. Retain temporary diagnostic work only when the approved plan includes it.

Stop as `Blocked` before continuing if evidence now indicates a materially different root cause or the fix requires a material change to scope, user-visible behavior, architecture or interfaces, dependencies, integrations or permissions, data handling or data model, migrations or rollout, security or privacy posture, or the approved fix strategy. Update both diagnosis and fix plan and obtain fresh direct approval before resuming.

### 7. Verify the fix

Verification must establish all applicable claims:

- the regression test or equivalent evidence failed for the diagnosed reason before the fix and passes after it;
- the original symptom is resolved in the relevant environment;
- focused and repository-required test, lint, type-check, build, migration, and other checks pass;
- no relevant check is unknown, skipped, stale, incomplete, or failing;
- the final diff matches the approved plan and excludes unrelated changes;
- temporary diagnostics were removed unless approved for inclusion.

Any relevant evidence gap is `Blocked`. Record the exact failure or unknown and the smallest action that could clear it. Do not create the finished PR while blocked.

### 8. Create and remotely verify the PR

After complete verification, push the intended commits and create one non-draft, ready-for-review PR against the intended base. The PR description preserves:

- diagnosis;
- approved fix plan;
- approval checkpoint without fabricated quotation or timestamp;
- actual changes;
- regression evidence;
- verification results;
- deviations from the approved plan;
- residual risks.

Fetch the PR from the remote service and verify repository, PR number, base branch, head branch, head SHA, non-draft state, title, and description. A successful creation command is not sufficient evidence.

If push, creation, or remote verification fails or differs, stop as `Blocked`, preserve the local work, and avoid blindly creating a duplicate PR.

After reporting the verified PR as `PR created`, stop. Never merge, enable auto-merge, or enter a merge queue.

## Material-Change Gate

A material change is any discovery that would make the approved diagnosis misleading or the approved fix plan no longer describe the work being performed. Material changes include:

- a different root cause or causal chain;
- changed scope or acceptance behavior;
- changed user-visible behavior;
- changed architecture, interfaces, dependencies, integrations, or permissions;
- changed data handling, data model, migration, or rollout;
- changed security or privacy posture;
- a different fix mechanism with materially different risk;
- temporary diagnostic work becoming production behavior.

When any trigger occurs: stop, show the new evidence, update both final artifacts, and obtain fresh direct approval.

## Artifact Structure

The portable package will contain:

```text
debug-with-evidence/
|-- SKILL.md
|-- agents/
|   `-- openai.yaml
`-- references/
    |-- acceptance-scenarios.md
    |-- diagnosis.md
    |-- fix-plan.md
    `-- pr-description.md
```

`SKILL.md` owns the state machine, authorization boundary, material-change gate, verification contract, terminal states, and point-of-need routing. The references define positive output contracts and behavioral evidence without duplicating the workflow. `agents/openai.yaml` contains only Codex-facing discovery metadata.

## Behavioral Validation

Create the skill with RED-GREEN-REFACTOR testing.

RED baselines should pressure an agent to:

- guess a fix from a stack trace without reproducing or isolating the cause;
- treat a workaround or correlation as proof;
- begin a production fix before approval because the change seems obvious;
- continue after implementation reveals a different root cause or fix strategy;
- open a PR despite missing relevant regression or environment evidence.

GREEN testing reruns the same scenarios with the skill loaded. Regression coverage should also verify:

- temporary diagnostics remain local before approval and are removed unless approved;
- automated regression coverage is preferred, with equivalent evidence only when automation is genuinely impractical;
- unrelated worktree changes remain untouched and excluded;
- the PR preserves the complete durable record;
- a verified PR is the stopping point and no merge-equivalent action occurs.

Observed choices and reasoning are recorded accurately. Skill changes are justified only by demonstrated failures or omissions.

## Acceptance Criteria

The skill is complete when:

- it validates as a portable Agent Skill;
- Codex metadata is isolated from the portable core;
- every RED scenario has preserved baseline evidence;
- every GREEN and regression scenario follows the required evidence and approval gates;
- unsupported root cause or verification claims produce `Blocked`;
- implementation cannot begin without direct approval of both final artifacts;
- material diagnostic or implementation drift requires updated artifacts and fresh approval;
- relevant verification gaps prevent PR creation;
- the PR is non-draft, remotely verified, and contains the durable debugging record;
- merge, auto-merge, and merge-queue actions are absolutely prohibited;
- independent review finds no open Critical or Important issue.
