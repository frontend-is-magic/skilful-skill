# Project Templates

Use these as starting templates. Trim unused pieces by project type. MVP docs are organized by phase and codename.

## Monorepo Layout

```text
.
|-- AGENTS.md
|-- docs/
|-- package.json
|-- pnpm-workspace.yaml
|-- turbo.json
|-- apps/
|   |-- web/
|   |-- api/
|   |-- desktop/
|   `-- mobile/
`-- packages/
    |-- config/
    |-- db/
    |-- types/
    |-- ui/
    `-- utils/
```

## Standard Scripts

Use this vocabulary at root when available:

```json
{
  "scripts": {
    "dev": "turbo dev",
    "build": "turbo build",
    "typecheck": "turbo typecheck",
    "lint": "turbo lint",
    "format": "prettier --write .",
    "format:check": "prettier --check .",
    "test": "turbo test",
    "test:e2e": "turbo test:e2e"
  }
}
```

For single-app repositories, keep the same command names but map them directly to that app's tooling.

## Env Files

- Keep `.env.example` in every app that reads environment variables.
- Never commit secrets.
- Validate boundary inputs with schema only where values cross runtime boundaries: env, HTTP, forms, external webhooks, files.

## AGENTS.md Outline

Include:

- Document Language: selected by conversation language, then user system/environment language, then explicit user choice.
- Project purpose and type.
- Stack and package manager.
- Directory ownership.
- Commands.
- Code style baseline and formatting.
- Git workflow and branch policy.
- Testing and CI gates.
- MVP codename series and naming rules, including the required codename for each MVP phase.
- MVP Docs Index: every MVP codename, status, technical plan link, task docs directory, and release status.
- Release Plan: normal release checklist for each MVP.
- Emergency Release Plan: hotfix flow from `main` through `hotfix/xxx`, PR back to `main`, release, then sync to `develop`.
- Task docs workflow: each MVP technical plan controls its task docs under `docs/mvp-<codename>/`.
- Known constraints and `To Confirm`.

Localize visible AGENTS.md section titles and prose to the selected document language, including MVP Docs Index, Release Plan, and Emergency Release Plan. Keep code, commands, paths, package names, API names, config keys, and error messages in their original English form.

## Docs Naming

Use codename directories for MVP phases:

```text
docs/mvp-<codename>/technical-plan.md
docs/mvp-<codename>/01-project-setup.md
docs/mvp-<codename>/02-api-contract.md
docs/mvp-<codename>/03-data-model.md
```

Prefer stable numbering by dependency order, not by urgency alone. Do not use numeric fallback directories such as `docs/mvp-01/`; every MVP phase must use a confirmed codename.
