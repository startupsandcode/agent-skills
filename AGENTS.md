# Agent Skills Repository Guidance

## Development workflow

- Create an isolated feature branch before changing this repository. Do not commit working changes directly to `main`.
- Preserve unrelated work and stage only intended paths.
- Before integration, inspect the complete feature-branch diff and run every relevant skill scenario, package validator, and repository check.
- Immediately before integration, revalidate that local `main` is clean, the inspected base and feature-head SHAs are unchanged, and the verification evidence still describes that exact tree. Repeat inspection and verification if any of them changed.
- Merge the feature branch into local `main` only after that revalidation passes, then push `main`.
- After pushing, fetch or query the remote and require the remote `main` SHA to equal the local merged SHA.
- Remove the finished worktree and feature branch only after remote SHA verification succeeds.
- If verification is incomplete or failing, stop and report the blocker instead of merging or pushing.

These instructions apply to work in the `agent-skills` repository. They do not change the authorization boundaries encoded inside individual skills for repositories where those skills are later used.
