# Agent Skills

Portable skills using the [Agent Skills](https://agentskills.io/) format, authored with Codex as the primary runtime.

## Install in Codex

Ask Codex to install an individual skill from this repository:

```text
$skill-installer install https://github.com/startupsandcode/agent-skills/tree/main/prepare-for-interview
```

Replace `prepare-for-interview` with any skill below. To install manually, clone or download this repository and copy the entire selected skill folder, including its references and metadata, into one of these locations:

- `<your-project>/.agents/skills/` for one repository.
- `~/.agents/skills/` for your user across repositories.

The resulting path should look like `.agents/skills/prepare-for-interview/SKILL.md`. Install each chosen folder individually; the repository root is not itself a skill. If the skill does not appear, restart Codex. See the [official skill installation and discovery documentation](https://learn.chatgpt.com/docs/build-skills#where-codex-loads-local-skills).

## Try a skill

In Codex CLI or the IDE extension, type `$` to select an installed skill, or include its name in your prompt as below. Supply the referenced files, links, or context with the request. These skills provide workflow instructions; connected services and repository access depend on your environment.

| Skill | Example prompt |
|---|---|
| [`inspect-and-finish-pr`](inspect-and-finish-pr/) | `$inspect-and-finish-pr review this PR, resolve actionable feedback, and verify it. Leave merging for my approval. PR: <URL>` |
| [`build-from-product-idea`](build-from-product-idea/) | `$build-from-product-idea help me build a client intake form in this repo. Shape the scope with me, then implement the approved plan and open a verified PR.` |
| [`debug-with-evidence`](debug-with-evidence/) | `$debug-with-evidence investigate why this CSV import duplicates contacts. Here are the reproduction steps and logs. Diagnose it and propose a fix before implementation.` |
| [`review-ui-against-requirements`](review-ui-against-requirements/) | `$review-ui-against-requirements review the onboarding flow against the attached requirements. Report gaps and propose the fix scope before changing code.` |
| [`daily-briefing`](daily-briefing/) | `$daily-briefing create today's brief from the calendar and task list below. Prioritize the client proposal, health, and anything needing a reply.` |
| [`deploy-and-verify`](deploy-and-verify/) | `$deploy-and-verify deploy commit <SHA> to this project's staging environment using its documented release process, then verify the login flow. This authorizes the staging deployment.` |
| [`prepare-for-interview`](prepare-for-interview/) | `$prepare-for-interview prepare me for a 45-minute engineering leadership interview using this job description and my resume. Include stories, questions to ask, and practice prompts.` |

## Skills

| Skill | Status |
|---|---|
| [`inspect-and-finish-pr`](inspect-and-finish-pr/) | Ready |
| [`build-from-product-idea`](build-from-product-idea/) | Ready |
| [`debug-with-evidence`](debug-with-evidence/) | Ready |
| [`review-ui-against-requirements`](review-ui-against-requirements/) | Ready |
| [`daily-briefing`](daily-briefing/) | Ready |
| [`deploy-and-verify`](deploy-and-verify/) | Ready |
| [`prepare-for-interview`](prepare-for-interview/) | Ready |
