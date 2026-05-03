# Task Docs Workflow

Use this reference after the current MVP technical plan exists or while writing it. Task docs belong to one MVP phase and are controlled by that phase's `technical-plan.md`.

## Goal

Turn the confirmed MVP technical plan into executable module-level task specs under `docs/mvp-<codename>/`.

## Document Language

Use the same document language chosen for `AGENTS.md` and the current MVP `technical-plan.md`. Localize task titles and visible section names. Keep code, commands, paths, package names, API names, config keys, and error messages in their original English form.

Name the unresolved-decisions section in the selected language. Use `To Confirm` for English documents.

## Required Flow

1. Read `AGENTS.md` and the current MVP `technical-plan.md`.
2. Infer task dimensions from the confirmed MVP scope.
3. Show the proposed dimensions and task list to the user.
4. Confirm details dimension by dimension.
5. Generate one Markdown file per task in the same MVP directory.
6. Add or update the task index in `technical-plan.md`.
7. Put unresolved decisions into `To Confirm`; do not invent them.

## Default Dimensions

Use only dimensions relevant to the MVP:

- Project setup and workspace.
- Web frontend.
- Backend API.
- Data model and migrations.
- API contract and client generation.
- Authentication and authorization.
- State management.
- Electron main/preload/renderer.
- React Native platform capabilities.
- Testing and quality gates.
- CI/CD and deployment.
- Documentation and release governance.
- Migration from previous MVP architecture.

## Task Doc Template

```markdown
# Task Title

## Goals

## Scope

## Prerequisites

## Implementation Notes

## Output Files

## Acceptance Criteria

## Testing Requirements

## AI Work Guidance

## Risks

## To Confirm
```

## Naming

Use ordered kebab-case filenames inside the current MVP directory:

```text
docs/mvp-<codename>/01-project-setup.md
docs/mvp-<codename>/02-web-frontend.md
docs/mvp-<codename>/03-backend-api.md
```

Order by dependency flow: setup before API, API/data before clients, implementation before tests/deploy.

## Confirmation Guidance

For each dimension, confirm only details that affect implementation:

- Scope included/excluded.
- Inputs/outputs or public interfaces.
- Dependencies on other dimensions.
- Acceptance criteria.
- Test expectations.
- Unknowns that should remain in `To Confirm`.
