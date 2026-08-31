# Briefing Automation

Read this reference for **Configure** or **Automate** mode.

## Briefing contract

Resolve only consequential unknowns. Offer labeled defaults, but do not invent locale, timezone, destinations, recipients, permissions, connected accounts, or sharing rules.

| Decision | Required result |
| --- | --- |
| Audience | Private brief, team-safe brief, or both |
| Time | Timezone, delivery schedule, and date boundary |
| Priorities | Current goals and what deserves interruption |
| Sources | Authorized inputs and retrieval windows |
| Selection | Urgency, deadline, blocker, conflict, and deferral rules |
| Delivery | Exact destination and recipients for each audience |
| Failure | Output when a source is partial, stale, unavailable, or failed |

An automation cannot activate until these values are known.

## Authorization boundaries

Connecting accounts, sending a real test, and activating a schedule are separate external actions. Each must be explicitly requested with its exact target. One request may authorize all three when it supplies all details; designing or drafting alone authorizes none.

Keep retrieval, generation, and delivery independently testable. Before activation, use non-delivery dry runs for current, empty, duplicate, partial, stale, and failed-source inputs. Send a real test only when that action and its exact destination are authorized.

Verify the confirmed timezone and schedule, every audience-specific destination, team-safe content rules, and degraded output. A successful scheduler or send command does not prove delivery; inspect the delivered artifact or provider delivery evidence before claiming end-to-end readiness.
