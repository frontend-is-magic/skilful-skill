# Baseline Stack

Use this reference after classifying a TypeScript project or when creating `AGENTS.md`.

## Project Type Classification

Classify from the user's description before selecting a stack:

| Type | Signals | Default stack |
| --- | --- | --- |
| Web frontend | UI, dashboard, admin, SPA, browser app, static client | Vite + React |
| Backend | API, service, worker, database, webhook, auth server | NestJS |
| Fullstack | UI plus owned API/database/business backend | Vite React + NestJS |
| Electron | desktop app, tray, native menus, local filesystem, packaged app | Electron + Vite |
| React Native | mobile app, iOS/Android, native device APIs | Expo React Native |

If the description mixes multiple types, choose the narrowest type that covers the delivery surface. Ask one clarification question when classification changes architecture.

## Workspace Defaults

Use `pnpm` workspaces and Turborepo for new multi-package projects.

Default full workspace:

```text
apps/
  web/
  api/
  desktop/
  mobile/
packages/
  ui/
  db/
  types/
  config/
  utils/
docs/
```

Trim unused apps and packages by project type.

## Package Boundaries

- `apps/*`: product entrypoints, routing, composition, platform glue.
- `packages/ui`: shared React UI primitives and shadcn/ui components.
- `packages/db`: Prisma schema, generated client wrapper, migration helpers.
- `packages/types`: shared DTOs, API types, domain types.
- `packages/config`: shared TypeScript, ESLint, Prettier, Tailwind config.
- `packages/utils`: pure shared utilities, Result helpers, small cross-platform functions.

Do not put platform-specific code into `packages/utils`. Keep Electron, browser, server, and React Native APIs behind app-level adapters unless a package is explicitly platform-scoped.

## Default Technology Choices

- Language: TypeScript-only, `strict` enabled.
- Web: Vite, React, React Router or TanStack Router only when routing complexity requires it.
- Backend: NestJS, REST controllers, OpenAPI generation.
- Data: Postgres + Prisma when persistence is required.
- API contract: REST + OpenAPI, with typed client generation or shared DTOs.
- Desktop: Electron + Vite, renderer follows Vite React standards.
- Mobile: Expo React Native.
- UI: Tailwind CSS + shadcn/ui for React UIs.
- Tooling: ESLint + Prettier.

## Existing Repositories

Inspect before applying defaults:

- package manager and lockfile.
- app/package structure.
- framework and build tool.
- scripts for typecheck, lint, format, test, build.
- current style rules and branch conventions.
- existing `AGENTS.md`, `docs/`, README, CI configs.

Prefer existing conventions unless they conflict with user-confirmed standards.
