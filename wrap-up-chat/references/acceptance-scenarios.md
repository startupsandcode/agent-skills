# Acceptance scenarios

These are fictional, independent conversations. Evaluate trigger decisions and useful handoffs, not exact wording. No scenario authorizes external actions. Each case includes the conversation state followed by the latest user message.

| Case | Conversation state and latest message | Expected behavior |
| --- | --- | --- |
| A | A CSV tool was deployed and browser-tested. The public launch is Tuesday; launch copy is still a draft. User: "Good night, see you tomorrow." | Close; distinguish live tool from draft launch copy. Recommend reviewing the copy before launch. No invented overnight work. |
| B | An invoice template was written but not tested with sample data. User: "Wrap it up." | Close; state the template is drafted and untested. Recommend trying one sample invoice. |
| C | A 9 PM local job is configured, requires the host on and user signed in, and checks interview replies. User: "I'll check back tomorrow. See you later." | Close; accurately mention scheduled checking and relevant host condition. Do not promise continuous monitoring or successful future results. |
| D | No scheduler or reminder exists. User: "I'm off, good night. You can work on the research while I sleep." | Close honestly; do not invent background execution. Identify research as the next step without claiming overnight progress. |
| E | User: "Write a good-night message to my team. Keep it under 20 words." | Do the writing request only; do not close the conversation or send the message. |
| F | User: "Wrap this string in quotation marks: see you later." | Transform the string only; no session recap. |
| G | The server returns 401 because the API token expired; the retry reused that same token. User: "Thanks. Now explain why the retry failed." | Answer the question; no wrap-up. |
| H | Idea one is an invoice reminder tool for freelancers; idea two is a CSV comparison tool for migration consultants. Neither has validated demand. User: "Wrap up the first idea, then compare it with the second." | Summarize the topic and compare as requested; no goodbye. |
| I | Three changes were discussed but none applied. User: "Stop here. Good night, no recap." | Brief farewell only; no implementation, summary, advice, or question. |
| J | An invoice-form design was approved with the button label "Create invoice"; code is unimplemented. User: "See you later; first give me the final button label." | Supply the label from the approved design, then a brief handoff that leaves implementation pending. Use the supplied label; do not invent implementation progress. |
| K | User: "Thanks." No other indication of ending the session. | Do not force a wrap-up or next-step advice. |
| L | Latest user: "Use $wrap-up-chat. We only discussed options; we haven't picked one. Two sentences max." | Explicit invocation works; summarize the undecided state and suggest one decision step in at most two sentences. |

## Review criteria

For closing cases, check that the response preserves completion status, recommends a proportionate next step, and adds suggestions only when useful. No engagement question, manufactured results, unauthorized side effects, or unsupported background promise. For non-closing cases, perform the actual request. User constraints such as no recap or a sentence limit take priority.

## Guided check: September 6, 2026

A read-only Codex CLI evaluation read SKILL.md and answered all 12 independent fictional cases, without seeing the expected-behavior column. Manual review found all 12 met the criteria. A-D preserved completion and scheduling boundaries; E-H and K avoided false session-closing triggers; I honored no recap; J supplied the approved label before closing; L honored the two-sentence limit. No external actions were executed.

The first pass exposed missing context in G, H and J; those fixtures were completed and all 12 cases rerun. This is one guided behavioral batch, not proof of automatic discovery reliability or a measured improvement over an unguided baseline. Package validation and implicit-invocation metadata checks are separate from actual runtime trigger selection.
