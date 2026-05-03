# MVP Planning Workflow

Use this reference before generating or updating `AGENTS.md`, every MVP technical plan, or per-MVP task docs.

## Document Language

Before writing an MVP technical plan, determine the document language:

1. Current conversation language.
2. User system or environment language.
3. Ask the user to choose a language.

Use the selected language for all prose and visible section titles in `technical-plan.md`. Keep code, commands, paths, package names, API names, config keys, and error messages in their original English form.

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

Record the chosen series and used codenames in `AGENTS.md`.

## Technical Plan Confirmation

Confirm the technical plan section by section. Do not batch all decisions into one unresolved blob.

Required sections to confirm:

- MVP goal and non-goals.
- Project type and target platforms.
- User/system workflows.
- Architecture and package boundaries.
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

## Data and Interfaces

## Task Docs Index

## AI Work Guidance

## Acceptance Criteria

## Release Plan

## Emergency Release Plan

## Risks

## To Confirm
```

## Release Planning

Every MVP must include an executable release checklist:

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
