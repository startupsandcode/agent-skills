---
name: wrap-up-chat
description: Close a conversation with a concise summary, a recommended next step, and useful contextual suggestions when the user says wrap it up, good night, see you later, or otherwise clearly ends the session. Do not trigger for quoted farewells, sign-off writing requests, routine thanks, or a topic change that continues the work.
---

# Wrap Up Chat

Leave the user with a clear sense of what happened and what is worth doing next, without turning a goodbye into more work.

## Recognize the closing intent

Use the latest message in context. Explicit requests such as "wrap up this chat" and personal farewells such as "I'm heading out, see you tomorrow" signal a close. "Thanks" alone, a farewell inside quoted text, "write a good-night message," and "wrap this string" do not. "Wrap up this topic, then help with the next one" continues the conversation; transition as requested instead of signing off.

If a closing message also includes a concrete task, handle that task within its existing scope before the wrap-up. Respect explicit stop or pause instructions and disclose unfinished work; do not press on with new tasks just to produce a complete-sounding summary. A goodbye does not cancel an already authorized schedule, but it does not create one either.

## Build a grounded handoff

Use the conversation's actual outcomes, decisions, user preferences, and remaining dependencies. Prefer the current state over a chronology of attempts. Distinguish completed and verified work from drafts, proposals, running jobs, and unverified results. Retain the most relevant link or artifact when it makes resuming easier. Do not claim to have rechecked live state unless you did.

Include:

- A brief summary of the meaningful result, or where the work stopped.
- One recommended next action for the user, with its reason or relevant timing. Favor a small concrete step over a broad productivity assignment. When the user has no useful action yet, say that instead of inventing homework.
- Up to two additional suggestions only when the context supports them: an unresolved decision, an overlooked dependency, a preparation step, or a sensible thing to defer. Omit these when they add nothing.

Keep recommendations distinct from commitments. Say what the user can do versus what the assistant is already scheduled or authorized to do. Mention genuine timing and execution conditions when they matter. Never promise overnight work, monitoring, reminders, notifications, or memory persistence without an established mechanism. A closing request alone does not authorize sending messages, scheduling jobs, committing files, or storing a summary.

## Deliver and stop

Use a warm, direct closing, normally two or three short paragraphs or a few bullets totaling roughly 60-140 words. Scale down for a small conversation; honor tighter limits or "no recap" immediately. No fixed headings are required. Avoid praise padding, a full task inventory, generic life advice, and repeating sensitive details that are unnecessary for the handoff.

Do not end with an engagement question or an offer to keep going. Identify a decision to revisit next time without requiring the user to answer now. Stop after the handoff. If the user resumes, continue naturally; do not keep repeating the wrap-up.

For maintenance, use [acceptance scenarios](references/acceptance-scenarios.md).
