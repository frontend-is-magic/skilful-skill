# MVP Planning Workflow

Use this reference before generating or updating `AGENTS.md`, every MVP technical plan, or per-MVP task docs.

## Document Language

Before writing an MVP technical plan, determine the document language:

1. Current conversation language.
2. User system or environment language.
3. Ask the user to choose a language.

Use the selected language for all prose and visible section titles in `technical-plan.md`. Keep code, commands, paths, package names, API names, config keys, and error messages in their original English form.

## Planning Boundary

This workflow creates planning documents only. Do not install packages, generate application scaffolds, write product source code, run codegen, create migrations, start development, launch implementation agents, or execute generated tasks.

## Project State

Treat the project as MVP 1 when:

- The repository is empty or has no major source code.
- `AGENTS.md` is missing.
- No MVP technical plan exists under `docs/`.

Treat it as MVP 2+ when there is an existing `AGENTS.md` plus at least one previous MVP plan. Before writing a later MVP plan, read:

- `AGENTS.md`.
- The previous MVP's `technical-plan.md`.
- Related docs from previous MVP directories.
- Package/app structure, key source files, tests, and build scripts relevant to the new scope.

After reading, summarize discovered architecture, completed scope, unresolved risks, and questions that need user confirmation.

## Codename Series

Every MVP phase must have a confirmed codename before its technical plan or task docs are created.

For a new project, propose 2-3 codename series based on product tone, domain, and visual style. Examples:

- Nordic myth realms for austere or mythical products.
- Space mission names for science, exploration, or infrastructure products.
- Studio album/session names for creative tools.

Ask the user to confirm the series before creating the first MVP directory. Use `docs/mvp-<codename>/` for each phase. Do not use numeric fallback directories such as `docs/mvp-01/` or `docs/mvp-02/`.

Record the chosen series and used codenames in `AGENTS.md`. Also update the top-of-file current MVP notice so it names the active MVP number, codename, status, technical plan path, and task docs directory.

## MVP 1 Git Setup

For MVP 1 only, this skill may prepare the repository's Git environment before writing planning docs:

- Run `git init` if the repository is not already initialized.
- Set the default branch to `main`.
- Create `develop` as the integration branch when the user wants the standard branch model.
- Record remote policy, branch policy, and release flow in `AGENTS.md`.

This Git setup must stop at repository and branch metadata. Do not create application source files, install dependencies, scaffold apps, run codegen, create migrations, or make development commits beyond planning documents.

## Confirmation Interaction

Confirm each planning section with the native choice mechanism required by `SKILL.md` for every decision that can be represented as finite choices. Use open-ended prompts only for product workflows, domain language, business rules, or goals that cannot be reduced to a helpful option set.

Require choice-based confirmation for:

- Document language when it is unclear.
- Project type and target platform.
- MVP codename series and current codename.
- Deployment/runtime target.
- Authentication and authorization depth.
- Persistence, storage, external APIs, jobs, and realtime scope.
- API contract and integration boundary.
- UI/design/accessibility constraints.
- Testing and CI gate level.
- Normal release and emergency release flow.
- Task dimensions, sequencing, and parallelization.

For each choice set, put the recommended default first and explain the tradeoff briefly. If a native choice tool supports only single-select, ask the user to select the closest option and add exceptions in free text. Keep unresolved or skipped decisions in `To Confirm`; do not invent decisions to avoid asking.

## Technical Plan Confirmation

Confirm the technical plan section by section. Do not batch all decisions into one unresolved blob.

Required sections to confirm:

- MVP goal and non-goals.
- Project type and target platforms.
- User/system workflows.
- Architecture and package boundaries.
- Environment initialization and local start scripts.
- Data model, persistence, and migrations.
- API contract and integration boundaries.
- Authentication and authorization.
- UI/design constraints when a client exists.
- Testing and CI gates.
- Release plan and emergency release plan.
- Task dimensions and acceptance criteria.

If the user has not decided a detail, write it under `To Confirm` instead of inventing it.

## Technical Plan Template

Each MVP technical plan lives at `docs/mvp-<codename>/technical-plan.md` and acts as the AI work entrypoint. The section names below are semantic placeholders; localize them to the selected document language.

```markdown
# MVP <Codename> Technical Plan

## Goals

## Non-Goals

## Current Repository Review Summary

## Confirmed Technical Plan

## Architecture and Directory Structure

## Environment Scripts

## Data and Interfaces

## Task Docs Index

## Task Phases And Parallelization

## AI Work Guidance

## Acceptance Criteria

## Release Plan

## Emergency Release Plan

## Risks

## To Confirm
```

After task docs are generated, update `Task Phases And Parallelization` with the planned dependency phases and per-phase parallel task groups.

The `Environment Scripts` section must define the planned responsibilities, prerequisites, platform differences, and acceptance checks for `init.sh`, `init.ps1`, `start.sh`, and `start.ps1`. Place script planning in the setup and governance phase by default.

## Release Planning

Every MVP must include a release checklist for future execution:

- Branch path.
- Required checks.
- Target environment.
- Data migration steps when applicable.
- Deployment steps.
- Post-release verification.
- Rollback entrypoint.

Default normal release flow: `develop -> main` PR.

Default emergency release flow:

1. Branch from `main` as `hotfix/xxx`.
2. Fix and verify the issue.
3. PR back to `main`.
4. Release from `main`.
5. Sync the fix back to `develop`.
6. Update affected MVP docs and release notes.
