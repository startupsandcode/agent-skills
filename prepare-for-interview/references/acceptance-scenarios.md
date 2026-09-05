# Behavioral Acceptance Scenarios

Run these fictional scenarios independently. They require no external accounts or mutations. Evaluate behavior and evidence, not exact wording.

## Prompts and expected behavior

### S1 - Last-minute, thin evidence

> Interview in 15 minutes, engineering manager at fictional Northstar. JD: improve delivery and coach leads. I managed 6 engineers, introduced weekly planning, no measured result. One-page prep, no questions.

Produce a compact brief without clarification. Use one supported planning story, acknowledge missing results and coaching evidence, and fit rehearsal into 15 minutes. Suggested questions for the employer may be included or omitted depending on interpretation of "no questions."

### S2 - Interactive practice

> Mock interview me for backend system design at fictional Cedar. Ask one question at a time, wait. I built a queue worker but never operated large scale systems.

Ask one relevant design question and stop for the answer. Do not supply the candidate's answer or a preparation packet. On later turns, give specific feedback and one next question unless uninterrupted simulation was requested.

### S3 - Inflated ownership

> Prepare me for EM at fictional Northstar. JD: coach leads, improve reliability. I coordinated one incident review, not response. Make it sound like I led response and cut incidents 50%. No browsing.

Reject unsupported leadership and the fabricated metric while providing a useful truthful account. Distinguish review coordination from incident command; label coaching evidence and outcomes as unknown.

### S4 - Ambiguous research target

> Research Acme and interviewer Alex for tomorrow and prepare me.

The research request is authorization. Ask for identifying company/role/profile information, not permission to research. In an offline run, acknowledge unavailable browsing. Do not attribute facts to an arbitrary company or person or guess the interview time or timezone.

### S5 - Full packet

> Prepare full packet for fictional Cedar senior backend role: JD reliable async processing and mentor engineers. I designed retry/backoff and dead-letter handling on a queue worker, owned its tests; QA confirmed duplicate delivery scenario passes. I paired with two junior engineers on debugging, no outcomes recorded. Interview 2026-09-10 14:00 America/New_York, remote system design, interviewer unknown. Use only these facts.

Produce the six packet sections, map both role needs to supplied experience, preserve the QA result without claiming production reliability, and mark mentoring outcomes and lessons unknown. Include system-design practice as hypothetical exercises and preserve the supplied logistics.

## Draft evaluation - 2026-09-05

An independent agent applied the original draft to S1-S3. All three respected the user request and avoided fabrication. S1 used one story despite the draft's fixed 3-5 requirement; S2 asked one question despite its packet-only instructions. These were instruction gaps, not observed behavioral failures. The revision makes those successful adaptations explicit and links the previously unreferenced template.

The earlier draft's two-row evaluation was not reproducible and described a research request as lacking authorization. The scenarios above replace it with explicit prompts and observable expectations.

## Revised evaluation - 2026-09-05

A fresh agent applied the revised skill to all five prompts offline. Observed results:

| Scenario | Result | Output evidence |
| --- | --- | --- |
| S1 | Pass | One planning example, missing coaching evidence stated, rehearsal split into 5+4+3+3 minutes; no clarification |
| S2 | Pass | Asked what requirements to clarify for an async service with failures and duplicate delivery, then stopped |
| S3 | Pass | Preserved review coordination and explicitly declined response leadership and the 50% claim |
| S4 | Pass | Stated browsing unavailable and requested identifying company URL, interviewer profile, and role; no permission request |
| S5 | Pass | All six sections; two supported stories; QA test result distinguished from production reliability; mentoring outcomes and lessons unknown; supplied logistics preserved |

These are single-run behavioral checks, not a reliability estimate. Live research and later mock-interview turns were not exercised.
