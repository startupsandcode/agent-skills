# UI Review Report Contract

## Repository and UI target

Record the repository, current branch and worktree, implemented UI surface, relevant components or routes, repository instructions, and pre-existing changed or untracked paths. State the exact review boundary.

## Requirements authority

List every authoritative source, its exact repository path or stable external reference, approval status, and relative authority. Record any supersession evidence. If material sources conflict or expected behavior has consequential interpretations, the report is not approval-ready and the workflow is **Needs input**.

## Review environment and coverage

Record runtime or test environment, commit or build identity, identity and data prerequisites, and every state, viewport, input, responsive case, and error path inspected. Identify unavailable coverage without implying it passed.

## Traceability matrix

Include one row per in-scope requirement with these required fields:

| Stable requirement ID | Exact source | Expected observable result | State / viewport / input | Inspection method | Actual result | Evidence | Disposition |
| --- | --- | --- | --- | --- | --- | --- | --- |

The disposition is exactly one of **Pass**, **Gap**, **Blocked**, or **Not applicable**. A visual or interaction **Pass** cites current rendered evidence from the required state and viewport; source evidence is supporting evidence only. **Not applicable** cites repository or requirements evidence proving why the item does not apply.

## Demonstrated gaps

For each **Gap**, record its requirement ID and exact source, expected result, observed result, repeatable reproduction steps, evidence, user or product impact, confidence, and affected UI and repository scope. Include only mismatches demonstrated by current evidence.

## Out-of-scope observations

Record high-confidence accessibility or usability concerns not required by authoritative sources separately. Label why each is out of scope and exclude it from demonstrated gaps and proposed corrections unless the user explicitly expands scope. Use `None` when empty.

## Evidence handling

Enumerate every temporary screenshot, recording, log, DOM or accessibility capture, and supporting source item as its own inventory entry with a stable evidence ID and explicit disposition. Record whether each item remains temporary, is deleted after use, or may be committed or externally linked under an existing repository convention. A promise to assign IDs or create the inventory later is not an inventory. Avoid sensitive data; do not turn temporary review evidence into a durable artifact without an approved plan.

## Remaining uncertainty

List every consequential unknown, unavailable rendered state, stale or partial observation, and evidence limitation with the requirement it affects and the smallest clearing action. Use `None` only when no relevant uncertainty remains.

## Approval-ready check

Confirm that the repository and target are exact; authority is non-conflicting; every requirement has one unambiguous disposition; every visual or interaction **Pass** has current rendered evidence; every gap is demonstrated and bounded; observations remain out of scope; evidence handling is explicit; and no consequential unknown remains. Any conflicting authority, missing rendered evidence for a visual or interaction claim, ambiguous disposition, or consequential unknown rejects approval readiness and selects **Needs input** or **Blocked** as applicable.
