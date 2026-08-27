# Implementation Plan Contract

## Repository evidence

Name the actual repository files, current behavior, tests, conventions, and relevant commands inspected. Distinguish observed evidence from assumptions.

## Affected components and files

List each expected component and file change with its purpose. Identify files that must remain untouched when relevant.

## Ordered implementation changes

List the smallest coherent implementation steps in dependency order, tied to the approved scope and acceptance criteria.

## Data flow and interfaces

Describe inputs, outputs, state changes, interface or API boundaries, and compatibility implications using repository evidence.

## Error handling

Describe expected failure modes, user-visible handling, logging or recovery behavior, and tests where applicable.

## Dependencies and permissions

Cover dependencies and permissions separately. For dependencies, list each required new or changed package, service, or integration with its purpose and impact; if no dependency applies, write `None` and explain why. For permissions, list each required new or changed access, credential, or privilege with its purpose and impact; if no permission applies, write `None` and explain why.

## Migrations and rollout

Cover migrations and rollout separately. For migrations, describe each data or schema migration, compatibility, rollback, and risk; if no migration applies, write `None` and explain why. For rollout, describe deployment sequence, release controls, and rollout risk; if no rollout work applies, write `None` and explain why.

## Test strategy

Map acceptance criteria and risk areas to repository-native automated and manual checks, including required environments or fixtures.

## Verification commands

Provide exact, runnable commands for all relevant checks, including acceptance verification and repository-required tests, lint, type checks, builds, migrations, or equivalent evidence. Do not substitute generic commands or mark a relevant check as optional without evidence.

## Material-change triggers

Stop for updated artifacts and fresh explicit approval if implementation would change scope; user-visible behavior; architecture or interfaces; dependencies, integrations, or permissions; data handling; migrations or rollout; or security or privacy posture.

## Approval-ready check

The plan is approval-ready only when it is grounded in actual repository evidence, specifies affected files and ordered changes, supplies exact verification commands, and explains all applicable delivery risks. Dependencies, permissions, migrations, and rollout must each be covered separately; for every individually non-applicable item, state `None` with reasoning. Present this final plan with the final product brief and wait for direct approval before implementation.
