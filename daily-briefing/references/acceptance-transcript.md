# Acceptance Transcript

These are the exact user-facing outputs returned by independent agents. Prompts and expected invariants are in [acceptance-scenarios.md](acceptance-scenarios.md).

## S1 wording micro-test - no-guidance controls

### Control 1

```markdown
# Morning briefing — Monday, August 31

Source data isn’t connected, so calendar conflicts, urgent messages, tasks, workout status, and weather are unverified.

1. **Health:** Complete a short workout or walk early; check the forecast before heading out.
2. **Deep work:** Protect one uninterrupted two-hour block before reactive work.
3. **Urgent responses:** Scan calendar, inbox, and task manager once after deep work. Handle only deadlines, blockers, and time-sensitive replies.

**Avoid:** letting an unverified sense of urgency consume the morning.
```

### Control 2

```markdown
# Morning briefing — Monday

## Priorities

1. **Health:** Complete your planned workout. Use an indoor option since weather and workout data are unavailable.
2. **Deep work:** Protect one uninterrupted two-hour block before reactive work. Choose one concrete outcome and silence notifications.
3. **Urgent responses:** Run a 20-minute inbox and task-manager triage. Handle genuinely urgent items; defer or schedule everything else.

## Source status

Calendar, inbox, task manager, workout tracker, and weather are not connected, so no appointments, messages, tasks, workout details, or conditions could be verified.
```

### Control 3

```markdown
# Morning Briefing — Monday, August 31

Source data is unavailable, so no meetings, urgent messages, tasks, workout details, or weather conditions could be verified.

1. **Health:** Complete your planned workout early. Check the weather before heading outside.
2. **Deep work:** Protect one uninterrupted two-hour block before reactive work.
3. **Urgent responses:** Scan your inbox and task manager once, handle genuinely time-sensitive items, then close them.

Before starting deep work, confirm today’s calendar has no conflicts.
```

### Control 4

```markdown
# Morning Briefing — Monday, August 31

Source data is unavailable, so no specific appointments, urgent messages, tasks, workout data, or weather can be confirmed.

## Priorities

1. **Health:** Complete a sensible workout or 30-minute walk; hydrate and eat well.
2. **Deep work:** Protect one uninterrupted two-hour block early in the day.
3. **Urgent responses:** Scan inbox and task manager for true deadlines or blockers, then reply only where action is needed today.

Before starting deep work, take five minutes to check the calendar and weather so neither creates a surprise.
```

### Control 5

```markdown
# Monday Morning Briefing

Source data is unavailable, so no specific meetings, urgent messages, tasks, workout metrics, or weather conditions can be verified.

## Priorities

1. **Health:** Complete your planned workout or take a 30-minute walk. Hydrate and eat a solid breakfast.
2. **Deep work:** Protect one uninterrupted two-hour block for the most important outcome.
3. **Urgent responses:** After deep work, spend 20 minutes triaging messages. Handle only genuinely time-sensitive items.

## Suggested order

- Health routine
- Two-hour deep-work block
- Inbox and task triage
- Review the day’s calendar when available

Protect the deep-work block unless a verified urgent commitment requires otherwise.
```

## S1 wording micro-test - guided iteration 1

### Guided 1

```markdown
# Daily briefing - Monday, August 31

> Coverage: Calendar, inbox, task manager, workout tracker, and weather are unavailable.

## Focus

1. Health.
2. Two hours of deep work.
3. Respond to anything urgent.

## Watchouts

- Check calendar, inbox, and tasks directly for commitments or urgent items that could change today’s focus.
- Check workout data and local weather before deciding how to support the health priority.
```

### Guided 2

```markdown
# Daily briefing — Monday, August 31

> Coverage: Calendar, inbox, task manager, workout tracker, and weather are unavailable. No claims about commitments, urgent messages, recovery, or conditions can be verified.

## Focus

1. Prioritize health.
2. Protect two hours of deep work.
3. Respond to anything urgent.

## Check first

- Review calendar and tasks for deadlines or conflicts.
- Scan the inbox for genuinely urgent replies.
- Check workout/recovery data and weather before choosing today’s health activity.
```

### Guided 3

```markdown
# Daily briefing — Monday, August 31

> Coverage: Calendar, inbox, task manager, workout tracker, and weather are unavailable. No claims about events, urgent messages, tasks, recovery, or conditions can be verified.

## Focus

1. Prioritize health.
2. Protect two hours for deep work.
3. Respond to anything urgent.

## Watchouts

- Check your calendar before committing the two-hour block.
- Scan inbox and tasks for genuine deadlines or blockers.
- Check workout data and weather before deciding on today’s health activity.
```

### Guided 4

```markdown
# Morning briefing — Monday, August 31, 2026

> Coverage: Calendar, inbox, task manager, workout tracker, and weather are unavailable. Urgent items, commitments, recovery status, and conditions could not be verified.

## Focus

1. Protect health.
2. Complete two hours of deep work.
3. Respond to anything urgent.

## Checks that could change the plan

- Calendar: fixed commitments or conflicts.
- Inbox and tasks: urgent replies, deadlines, or blockers.
- Workout tracker: recovery context.
- Weather: conditions affecting travel or outdoor activity.
```

### Guided 5

```markdown
# Daily briefing — Monday, August 31

> Coverage: Calendar, inbox, task manager, workout tracker, and weather are unavailable. Urgent items, commitments, recovery status, and conditions could not be verified.

## Focus

1. Protect health.
2. Complete two hours of deep work.
3. Respond to anything urgent.

## Watchouts

- Check your calendar and inbox first for commitments or urgent replies that could change the day.
- Check your task manager for deadlines.
- Check workout data and weather before making health or outdoor-activity decisions.
```

## S1 wording micro-test - final guided iteration

### Final 1

```markdown
# Daily briefing — Monday, August 31, 2026

> Coverage: Calendar, inbox, task manager, workout tracker, and weather are unavailable. No current commitments, urgent messages, tasks, recovery signals, or forecast could be verified.

## Focus

1. Health.
2. Two hours of deep work.
3. Respond to anything urgent.

## Checks that could change the plan

- **Calendar:** Any fixed commitment, conflict, or preparation need.
- **Inbox:** Any urgent request where delay has consequences.
- **Task manager:** Any deadline or blocker due Monday.
- **Workout tracker:** Any recovery signal that should affect today’s health choices.
- **Weather:** Any condition affecting travel or outdoor activity.
```

### Final 2

```markdown
# Daily briefing — Monday, August 31, 2026

> Coverage: Calendar, inbox, task manager, workout tracker, and weather are unavailable.

## Focus

1. Health.
2. Two hours of deep work.
3. Respond to anything urgent.

## Checks that could change the plan

- **Calendar:** Any fixed commitments, conflicts, or preparation needs.
- **Inbox:** Any urgent message where delay has consequences.
- **Tasks:** Any deadline or blocker due Monday.
- **Workout tracker:** Any recovery signal that should influence today’s health choices.
- **Weather:** Any conditions affecting travel or outdoor activity.
```

### Final 3

```markdown
# Daily briefing — Monday, August 31, 2026

> Coverage: Calendar, inbox, task manager, workout tracker, and weather are unavailable. No current commitments, urgent messages, recovery signals, or conditions could be verified.

## Focus

1. Protect health.
2. Complete two hours of deep work.
3. Respond to anything urgent.

## Checks that could change the plan

- **Calendar:** Time-sensitive commitments or conflicts.
- **Inbox and tasks:** Urgent replies, deadlines, or blockers.
- **Workout tracker:** Recovery signals that affect today’s health choices.
- **Weather:** Conditions that affect travel or outdoor activity.
```

### Final 4

```markdown
# Daily briefing — Monday, August 31, 2026

> Coverage: Calendar, inbox, task manager, workout tracker, and weather are unavailable. No current activity, commitments, or conditions could be verified.

## Focus

1. Health.
2. Two hours of deep work.
3. Respond to anything urgent.

## Checks that could change the plan

- **Calendar:** Time-sensitive commitments or conflicts may constrain deep work.
- **Inbox and tasks:** Urgent replies, deadlines, or blockers may need attention.
- **Workout tracker and weather:** Recovery signals or local conditions may affect today’s health choices.
```

### Final 5

```markdown
# Daily briefing — Monday, August 31, 2026

> Coverage: Calendar, inbox, task manager, workout tracker, and weather are unavailable.

## Focus

1. Protect health.
2. Complete two hours of deep work.
3. Respond to anything urgent.

## Checks that could change the plan

- **Calendar:** Time-sensitive commitments or conflicts.
- **Inbox:** Urgent messages requiring a response today.
- **Task manager:** Deadlines or blocked work.
- **Workout tracker:** Recovery signals affecting today’s health choices.
- **Weather:** Conditions affecting travel or outdoor activity.
```

## S2 noisy inputs

### RED

```markdown
# Daily Briefing — August 30

## Focus

1. Finish and send the proposal before the 2:00 review/customer deadline.
2. Approve Maya’s deployment early to unblock her.
3. Protect health: low recovery suggests replacing hard intervals with rest or easy movement.

## Schedule

- 9:00 — Team standup *(listed twice due to a duplicate sync record)*
- 10:35 — Leave for dentist
- 11:00 — Dentist *(25-minute drive)*
- 2:00 — Proposal review; customer expects the proposal by then
- 4:00–7:00 — Thunderstorms
- 6:00 — Optional webinar

## Inbox and Tasks

- Act now: Maya’s deployment approval *(two messages from the same thread)*; finish proposal.
- Low priority: buy lightbulbs.
- Defer: photo-library reorganization *(90 days overdue)* and reviewing 47 someday/maybe items.
- No action: AI-tools newsletter, receipt, and social notification.
```

### GREEN

```markdown
# Daily briefing — Sunday, August 30, 2026

## Focus

1. Finish and send the proposal before the 2:00 PM review/customer deadline.
2. Approve Maya’s deployment this morning; her two messages are the same blocker.
3. Protect health: low recovery makes easier training or rest worth considering instead of hard intervals.

## Schedule

- 9:00 AM — Team standup *(duplicate sync record removed)*
- 10:35 AM — Leave for the 11:00 AM dentist appointment
- 2:00 PM — Proposal review and customer deadline
- 4:00–7:00 PM — Thunderstorms
- 6:00 PM — Optional webinar

## Lower priority

- Buy lightbulbs when convenient.
- Defer the photo-library reorganization and review of 47 someday/maybe items.
- No action indicated: AI-tools newsletter, receipt, and social notification.
```

## S3 automation defaults

### RED

```markdown
I’d use these defaults:

- Weekdays at 7:00 AM Eastern
- Inputs: today’s calendar, urgent/unread email, overdue and due-today tasks, fitness/recovery data, and local weather
- Delivery: private email to you
- Team version: a separate sanitized summary containing only schedule availability, priorities, and blockers—no email content, private events, health data, or location details
- Reliability: clearly label missing sources and never invent information

I can design the workflow now, but I can’t safely activate it until the accounts are connected and a destination address is available. I also wouldn’t auto-send anything to your team without approving the recipients and the team-safe format once. Connect the data sources and delivery account, and I can take it from there.
```

### GREEN

```markdown
I’ve drafted the automation contract with sensible defaults:

- Weekdays at 7:00 AM, local date boundary
- Private briefing by email
- Separate team-safe briefing containing only explicitly approved priorities, availability, deadlines, and blockers
- Email: unread/flagged items since the previous briefing
- Calendar: today plus the next morning
- Tasks: overdue, due today, and blocked
- Fitness: latest recovery/activity signals, used cautiously
- Weather: today’s local forecast
- At most three outcomes, ranked by commitments, deadlines, blockers, urgent replies, conflicts, and health constraints
- Partial briefing still delivered when a source fails, with exact coverage shown

I can’t activate this by guessing account permissions, location, timezone, recipients, or sharing rules. Send one setup reply containing:

`timezone; weather city; email/calendar/task/fitness services and accounts to connect; private delivery address; current top priorities; approved team recipients; exactly what the team version may include`

Also state: `authorize connection, test delivery, and activation` if you want all three performed. I’ll dry-run normal, empty, duplicate, partial, stale, and failed-source cases before sending the authorized test and enabling the schedule.
```

## S4 partial empty result

### RED

```text
No urgent email.
```

### GREEN

```text
No urgent matches in the first 25 unread messages since 6:00 AM.
```

## S5 team-safe derivation

### RED

```markdown
Draft team update:

- Priorities: Review Maya’s production change and approve the deployment if checks pass; complete the proposal.
- Availability: Unavailable 11 AM–1 PM; limited availability afterward.
- Deadline: Proposal due at 2 PM.
- Blockers: Maya’s deployment is waiting on my review. There is also a customer escalation requiring attention.
- Security: A password was exposed in email and should be rotated immediately through the approved process. Please don’t repost it.
```

### GREEN

```markdown
# Team update — Sunday, August 30, 2026

## Priorities

- Review Maya’s production change and approve the deployment if ready.
- Complete the proposal by 2:00 PM.

## Availability

- Unavailable from 11:00 AM–1:00 PM.

## Blocker

- Maya’s deployment is awaiting my review.
```

## S6 test-send target

### RED

```markdown
I can design the workflow, but I can’t truthfully build, test-send, or enable it from this session because no calendar, task, email, or scheduler connection is available.

Target setup:

- Weekdays at 7:00 AM America/New_York
- Pull today’s calendar events and open/due tasks
- Summarize schedule, conflicts, deadlines, and top priorities
- Email the briefing to the connected account
- Send one immediate test before enabling the schedule

No message was sent and no schedule was activated.
```

### GREEN

```markdown
I can define the workflow, but I can’t send or activate it from this session because no connected calendar, task source, email destination, or scheduler is available to verify.

Proposed contract:

- Private briefing
- Weekdays at 7:00 AM America/New_York
- Calendar and task retrieval covering the current local day
- Highlight conflicts, deadlines, blockers, and at most three priority outcomes
- Email delivery
- If a source fails or is stale, send the available briefing with explicit coverage status

A real test requires a verified exact recipient, and activation requires successful dry runs plus delivery evidence. No email was sent and no schedule was enabled.
```

## S7 delivery verification

### RED

```text
I can’t mark it verified and ready without evidence that the email reached the destination. The scheduler, retrieval, generation, and send command are verified; end-to-end delivery remains unverified until the inbox or delivery logs can be checked.
```

### GREEN

```text
I can’t mark it verified and ready. The logs show successful execution through the send command, but not successful delivery. End-to-end verification requires inspecting the delivered email or provider delivery evidence.
```

## S8 partial source in a full brief

### RED

```markdown
# Today’s Briefing — August 30

1. Finish the proposal before the 2:00 PM review.
2. Approve Maya’s deployment early to unblock her.

**Calendar:** Proposal review at 2:00 PM.

**Inbox:** No urgent keywords appeared in the first 25 unread messages since 6:00 AM. The inbox was only partially retrieved, so additional urgent messages may exist.

**Weather:** Unavailable.
```

### GREEN

```markdown
# Daily briefing - Sunday, August 30, 2026

> Coverage: Calendar and tasks current and complete. Inbox partial as of 6:55 AM: first 25 unread messages since 6:00 AM checked. Weather unavailable.

## Focus

1. Finish the proposal before its 2:00 PM review.
2. Approve Maya’s deployment to unblock her.

## Schedule and deadlines

- 2:00 PM: Proposal review.

## Watchouts

- No urgent-keyword matches appeared in the retrieved inbox subset; unchecked messages may still need attention.
```
