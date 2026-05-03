# New Repo Questionnaire

Ask only what cannot be inferred from the repository or user's project description. Keep the first pass concise.

## Universal Questions

1. What is the primary project type: Web frontend, Backend, Fullstack, Electron, or React Native?
2. What is the MVP user or system workflow?
3. Is this a new repo or an existing repo with conventions to preserve?
4. Which deployment/runtime target matters first?
5. Does the project need authentication or role/permission modeling?
6. Does it need persistence, external APIs, file storage, jobs, or realtime features?
7. What level of tests and CI gates are required for the first milestone?
8. Are there design system, brand, accessibility, or platform constraints?

## Web Frontend

Default: Vite + React + TypeScript + Tailwind + shadcn/ui.

Confirm:

- SPA only, or does it need a separate API/backend?
- Routing complexity and protected routes.
- Server data fetching approach.
- Form validation and schema needs.
- Browser support and responsive breakpoints.

## Backend

Default: NestJS + TypeScript.

Confirm:

- REST API, background worker, webhook service, or mixed service.
- Persistence model and database ownership.
- Authn/authz strategy.
- OpenAPI requirements and client consumers.
- Logging, metrics, queues, scheduled jobs, and file handling.

## Fullstack

Default: Vite React frontend + NestJS backend.

Confirm:

- Deployment split: separate frontend/backend or unified platform.
- API ownership and OpenAPI client generation.
- Shared types boundary.
- Auth session/token flow.
- Database schema ownership and migrations.

## Electron

Default: Electron + Vite + TypeScript.

Confirm:

- Local-only app or app with remote backend.
- Main/renderer/preload boundaries.
- Filesystem, native menus, tray, auto-update, signing/notarization.
- Renderer UI stack, default Vite React unless user says otherwise.

## React Native

Default: Expo React Native + TypeScript.

Confirm:

- iOS, Android, or both.
- Backend/API ownership.
- Native capabilities: camera, push notifications, storage, location, biometrics.
- Offline mode and local persistence.
- Distribution target: dev build, TestFlight, Play Store, internal.
