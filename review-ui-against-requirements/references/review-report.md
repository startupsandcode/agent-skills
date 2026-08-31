# UI Review Report Contract

## Repository and UI target

Record the repository, current branch and worktree, implemented UI surface, relevant components or routes, repository instructions, and pre-existing changed or untracked paths. Record the sanitized remote identity, intended base/default branch, current HEAD, intended distinct head, upstream, merge base, and pre-existing base-to-head commits. State the exact complete review boundary.

## Requirements authority

List a non-empty set of authoritative sources, each source's exact repository path or stable external reference, approval status, and relative authority. Record any supersession evidence. If the set is empty, approval or relative authority cannot be established, material sources conflict, or expected behavior has consequential interpretations, the report is not approval-ready and the workflow is **Needs input**.

## Review environment and coverage

Record runtime or test environment, commit or build identity, identity and data prerequisites, and every state, viewport, input, responsive case, and error path inspected. Identify unavailable coverage without implying it passed.

## Traceability matrix

Include one row per in-scope requirement with these required fields:

| Stable requirement ID | Exact source | Expected observable result | State / viewport / input | Inspection method | Actual result | Evidence | Disposition |
| --- | --- | --- | --- | --- | --- | --- | --- |

The disposition is exactly one of **Pass**, **Gap**, **Blocked**, or **Not applicable**. A visual or interaction **Pass** cites current rendered evidence from the required state and viewport; source evidence is supporting evidence only. **Not applicable** cites repository or requirements evidence proving why the item does not apply.

The matrix must contain at least one observable in-scope requirement. An empty matrix, or authoritative sources from which no observable UI requirement can be derived without invention, is not approval-ready and selects **Needs input**.

## Demonstrated gaps

For each **Gap**, record its requirement ID and exact source, expected result, observed result, repeatable reproduction steps, evidence, user or product impact, confidence, and affected UI and repository scope. Include only mismatches demonstrated by current evidence.

## Out-of-scope observations

Record high-confidence accessibility or usability concerns not required by authoritative sources separately. Label why each is out of scope and exclude it from demonstrated gaps and proposed corrections unless the user explicitly expands scope. Use `None` when empty.

## Evidence handling

Enumerate every temporary screenshot, recording, log, DOM or accessibility capture, and supporting source item as its own inventory entry with a stable evidence ID and explicit disposition. Record whether each item remains temporary, is deleted after use, or may be committed or externally linked under an existing repository convention. A promise to assign IDs or create the inventory later is not an inventory.

Sanitize every artifact before presentation or persistence, including command output, logs, URLs and query strings, headers, cookies, screenshots, and identity or customer data. For credentials, record only a non-sensitive identifier, approved secure source, required scope, and availability; never record a value, fragment, signed URL, or session material. If exposure is detected, the workflow is **Blocked** and publication is prohibited. Identify the item without repeating it and name the separately authorized rotation or revocation action; do not perform it under review approval.

## Remaining uncertainty

List every consequential unknown, unavailable rendered state, stale or partial observation, and evidence limitation with the requirement it affects and the smallest clearing action. Use `None` only when no relevant uncertainty remains.

## Approval-ready check

Confirm that the repository and target are exact; the authoritative source set is non-empty with established approval and relative authority; the matrix has at least one observable in-scope row; every requirement has one unambiguous disposition; every visual or interaction **Pass** has current rendered evidence; every gap is demonstrated and bounded; observations remain out of scope; evidence is sanitized and its handling is explicit; and no consequential unknown remains. An empty authority set, absent observable requirement, unresolved approval or relative authority, conflicting authority, ambiguous disposition, or missing expected behavior selects **Needs input**. Missing required evidence or exposed private data selects **Blocked**.

If every row is **Pass** or evidence-backed **Not applicable** and no consequential uncertainty remains, select **Review complete** and stop without a fix plan, approval request, repository change, commit, push, or PR. Otherwise preserve the complete matrix, including every demonstrated gap, for the fix plan and durable PR record.
