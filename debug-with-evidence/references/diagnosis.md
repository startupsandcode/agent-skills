# Diagnosis contract

Use this artifact to present the approval-ready diagnosis. Record exact commands/actions and actual outputs. Label each claim as Fact, Inference, or Unknown. Do not claim causality from a stack location, correlation, or workaround.

## Reported symptom

- Fact: <reported failure or unexpected result>

## Expected behavior

- Fact: <expected result>

## Repository and environment

- Fact: <repository, branch/worktree, version, configuration, and relevant environment>

## Reproduction

- Command/action: `<exact command or action>`
- Actual output/result: <verbatim or faithful result>
- Frequency: <observed frequency, or Unknown>

## Observations

- Fact: <boundary observation and evidence>

## Hypotheses tested

- Hypothesis: <competing explanation>
- Discriminating command/action: `<exact command or action>`
- Actual result: <output/result>
- Conclusion: <supported, ruled out, or still unknown>

## Root-cause chain

- Fact: <observed failure>
- Inference: <supported transition through each relevant boundary>
- Fact: <originating defect and evidence>

## Affected scope and blast radius

- Inference: <bounded affected components, users, data, and failure modes>

## Remaining uncertainty

- Unknown: <uncertainty, impact, and why it is or is not consequential>

## Temporary diagnostics

- Path: `<path>`
- Purpose: <local diagnostic purpose>
- Disposition: <remove before commit, or retain only if the approved plan gives lasting regression/observability value>

## Approval-ready check

- Supported causal chain to originating defect: <Yes/No>
- Bounded blast radius: <Yes/No>
- Consequential unknowns resolved: <Yes/No>
- Every temporary path has a disposition: <Yes/No>
- Result: <Approval-ready, Blocked, or Needs input>. Unsupported causality, unbounded blast radius, or a consequential unknown is not approval-ready; use **Blocked** or **Needs input** according to the missing condition.
