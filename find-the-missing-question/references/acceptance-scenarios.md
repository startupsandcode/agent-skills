# Acceptance Scenarios

Use each prompt independently, first without the skill and then with it. Evaluate actual responses rather than checking for matching headings. These fictional scenarios require no external actions.

## Prompts

### A - Output versus benefit

> All seven agent skills pass their validators and guided scenarios. Write a concise recommendation on whether we should spend next week building seven more. Our aim is better task outcomes; we have no unguided runs.

### B - Solution before diagnosis

> Users abandon checkout. Five interviewed users asked for a chatbot. We have one week to increase completed purchases. What should we do next?

### C - Mechanical task

> Fix this typo only: The report is publsihed every Friday.

### D - Settled decision

> We already tested self-service onboarding against assisted onboarding: activation unchanged, support workload fell 40%. Decision is made. Give me a three-step rollout checklist, no strategy review.

### E - Metric mismatch

> We need to reduce customer response time. Dashboard median is two hours, but customers say they wait days. What question are we missing? Give me a small test, no new instrumentation project.

## Review criteria

For A, B, and E, look for a grounded uncertainty that could change the next action, a bounded test with observable evidence, and actions for supporting, contrary, and inconclusive results. Preserve uncertainty and avoid claiming a small sample proves a broad effect. For C, return only the corrected sentence. For D, provide the requested rollout checklist without reopening the decision. No scenario authorizes contacting customers or changing live systems.

## Baseline observations - 2026-09-06

One independent agent answered all five prompts without the skill. It correctly identified the core uncertainty in A, B, and E and respected scope in C and D. The basic ability to spot these assumptions already existed.

- A recommended comparing completion, correctness, rework, and time with and without skills, but provided no sample/time bound or explicit inconclusive-result action.
- B bounded initial investigation to one day, suggested observing purchases and testing a small fix, and kept a chatbot conditional. It did not specify what to do if no clear obstacle emerged.
- C returned exactly: "The report is published every Friday."
- D supplied a three-step rollout checklist with staged expansion and checks.
- E proposed tracing 10 requests, including open cases, against first contact, first useful answer, and resolution. It named plausible causes but did not map observations to specific next actions or cover inconclusive results.

The skill targets the incomplete connection between a proposed test and a decision. These observations do not establish a general deficiency or prove that adding a skill will improve real task outcomes.

## Guided observations - 2026-09-06

A fresh agent read the skill and answered the same five prompts, with the same 160-word response limit.

| Scenario | Observed behavior | Assessment |
| --- | --- | --- |
| A | Proposed one day of paired runs, two tasks per skill, comparable conditions and anonymized review; mapped clear gains, mixed results, and inconclusive findings to different investments | Pass; feasibility still depends on task duration |
| B | Bounded initial review to one day and up to 20 abandonments plus five observations; kept chat conditional on unanswered questions and defect fixes conditional on observed defects; retained a small pilot if inconclusive | Pass; proposed user observation and pilot are not executed or authorized by this evaluation |
| C | Returned only "The report is published every Friday." | Pass |
| D | Returned three rollout steps; did not reopen the strategy decision | Pass |
| E | Proposed one hour and 15 requests including open cases and complaints; separated excluded/automatic-reply cases from long-tail waits; proposed five complaint-history reviews if unexplained | Pass; purposive sample supports diagnosis, not a population estimate |

Compared with this baseline, the guided outputs made test bounds and conditional next actions more explicit without derailing C or D. Both conditions already found the main uncertainties. This is a single paired evaluation batch, not repeated fresh samples or measured downstream outcomes. Live execution, automatic discovery, and long-term interruption cost remain untested.
