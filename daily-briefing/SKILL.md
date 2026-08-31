---
name: daily-briefing
description: Use when a user wants a concise daily or morning briefing produced from personal sources, or wants a repeatable briefing workflow designed or automated.
---

# Daily Briefing

Turn current personal signals into a short decision aid. The briefing should reduce attention, not reproduce every source.

**Core principle:** Compress verified evidence into today's priorities, constraints, and actions. Never simulate unavailable data.

## Choose the mode

- **Produce:** Generate a briefing now from the user's supplied or connected sources.
- **Configure:** Define a reusable briefing contract for this person.
- **Automate:** Implement or revise a scheduled workflow using the approved contract and the tools available in the user's environment.

If a reusable contract exists, follow it. A one-off brief may degrade gracefully. For **Configure** or **Automate**, read [automation.md](references/automation.md) before proposing or changing the workflow.

## Build from evidence

1. Determine the briefing date, timezone, source retrieval window, and current priorities.
2. Classify every expected source as **current and complete**, **current and complete with no matching items**, **partial**, **stale**, **unavailable**, or **failed**. Record the retrieval window and scope when they affect meaning.
3. Normalize times, remove duplicate events or messages, connect related evidence, and distinguish facts from suggestions.
4. Rank by the user's priorities and the consequence of delay or omission. Typical signals include commitments, deadlines, blockers, urgent replies, conflicts, preparation or travel time, health constraints, and useful context.
5. Select at most three outcomes. Defer or omit low-value inputs instead of giving every item equal weight.
6. Check each claim against a source. Include an `as of` time when freshness matters.

Evidence controls specificity. A user-stated priority supports repeating that priority, but not inventing its activity, timing, duration, or order. When operational sources are unavailable, keep the priority at the user's level of abstraction and tell them which direct checks could change the plan; do not add a suggested schedule.

For a degraded brief, use this positive shape: a title containing the resolved weekday, month, day, and year; a coverage notice; the user-stated focus; then source-labeled **Checks that could change the plan**. Phrase those checks as conditions, not a sequence. Words such as `first`, `before`, and `after` require current evidence that supports that order.

An empty-result claim is valid only when the retrieval window, filters, pagination, and accessible scope are sufficient for that claim. Otherwise report the result as partial: "No urgent matches in the first 25 unread messages since 6:00 AM," not "No urgent email."

Treat fitness or health data as context, not diagnosis. Use cautious options when it materially changes the day. Never expose private event details, messages, health data, location, or credentials in a shared version.

## Output contract

Return the smallest useful version of this shape:

```markdown
# Daily briefing - Monday, August 31, 2026

> Coverage: Calendar and tasks current as of 6:55 AM. Email unavailable.

## Focus
1. Finish the proposal before its 2:00 PM review.
2. Approve Maya's deployment request this morning.
3. Protect recovery; consider an easier training option.

## Schedule and deadlines
- 10:35 AM: Leave for the 11:00 AM dentist appointment.
- 2:00 PM: Proposal review and customer deadline.

## Watchouts
- Thunderstorms are expected from 4:00-7:00 PM.
```

Omit empty sections. Put source coverage near the top when any expected source is partial, stale, unavailable, or failed. Use absolute dates and local times. Keep recommendations traceable to evidence and clearly phrased as suggestions.

For a team-safe briefing, create a separate artifact and apply sharing rules to every item's content, not just its category. Approval to share "availability" does not approve embedded health, location, message, credential, or private-event details. Exclude secrets. Generalize a private cause only when the source already states a useful operational fact independent of it; never infer a new shareable fact from sensitive context. Otherwise omit it or ask.

## Common mistakes

| Mistake | Correction |
| --- | --- |
| Treating an unavailable or partial inbox as empty | State its exact coverage and avoid broader claims |
| Turning a broad priority into an unsupported plan | Keep it at the stated abstraction until current evidence supports a tactic or time |
| Listing every event, task, and message | Select only items that change today's decisions |
| Sharing an approved category with private details inside it | Apply approval to each item's content and generalize, omit, or ask |
