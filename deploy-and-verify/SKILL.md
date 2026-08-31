---
name: deploy-and-verify
description: Use when a user asks to deploy, release, promote, roll back, or verify one application version in a named environment.
---

# Deploy and Verify

Move one known version to one known environment, then establish current evidence of the resulting behavior. A deploy command is an action record, not proof that users can use the release.

## Establish the release

Identify the application, environment, exact artifact or revision, deploy mechanism, expected user-visible behavior, and rollback candidate. Read repository and platform instructions before any mutation. Record the current deployed revision if it can be observed.

Ask for a consequential missing decision; do not guess a production target, branch, artifact, account, region, or rollback version. A user may authorize a deployment, but rollback, traffic changes, destructive data operations, and credential changes require their own explicit authorization unless the user explicitly included them.

## Deploy with a bounded record

Before invoking a deploy, confirm that the intended revision matches the approved release and that the command targets only the named environment. Preserve the exact command result, release identifier, time, and deployment URL or provider record.

If deployment fails or returns an ambiguous result, stop as **Blocked**. Inspect the provider state before retrying; never blindly rerun a deploy or substitute another target.

## Verify the release

Verify the claims that matter for this release using current evidence from the deployed environment:

| Claim | Evidence |
| --- | --- |
| Correct version | Runtime, provider, or release identifier matches the intended revision |
| Reachability | Relevant endpoint or UI responds in the deployed environment |
| Core behavior | A release-specific smoke check succeeds without test-only shortcuts |
| Safety signals | Relevant health, error, or log signals show no new blocking condition |

Use the smallest representative checks for the change. Treat missing access, a pending rollout, a failed check, stale evidence, or a successful command without observed behavior as **Blocked**. Do not announce a release as verified from deployment status alone.

## Rollback and incidents

If a credible regression appears, preserve evidence and identify the current and proposed rollback revisions. Execute rollback only with explicit rollback authorization for the named environment and revision. After a rollback, verify the restored behavior just as you would a forward deploy.

## Report one state

- **Deployed and verified:** report application, environment, intended and observed revision, deployment record, checks run, and their current evidence.
- **Blocked:** report the exact missing or failing evidence, current deployed state if known, preserved work, and the smallest safe next action.

## Common mistakes

| Mistake | Correction |
| --- | --- |
| Treating a command exit code as release verification | Check current deployed behavior and version |
| Guessing the usual production target | Stop for the exact application, environment, and revision |
| Retrying after an ambiguous deploy | Inspect provider state before any further mutation |
| Treating urgency as rollback authorization | Obtain explicit authorization for the named rollback |
