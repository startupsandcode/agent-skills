# Agent Skills Repository Guidance

## Development workflow

- Create an isolated feature branch before changing this repository. Do not commit working changes directly to `main`.
- Preserve unrelated work and stage only intended paths.
- Before integration, inspect the complete feature-branch diff and run every relevant skill scenario, package validator, and repository check.
- Merge the feature branch into local `main` only after that inspection passes, then push `main`.
- If verification is incomplete or failing, stop and report the blocker instead of merging or pushing.

These instructions apply to work in the `agent-skills` repository. They do not change the authorization boundaries encoded inside individual skills for repositories where those skills are later used.
