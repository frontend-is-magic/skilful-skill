---
name: mvp-creator
description: Use when defining TypeScript MVP plans and planning documents across Web frontend, Backend, Fullstack, Electron, and React Native; when generating AGENTS.md, MVP technical plans, docs/mvp-* task specifications, release plans, emergency hotfix plans, or AI handoff guidance for staged product delivery.
---

# MVP Creator

Use this skill to turn a TypeScript product idea or existing repository into staged MVP planning documents. The skill owns only the planning layer: classify the project, confirm the current MVP phase, prepare allowed MVP 1 Git setup, generate or update `AGENTS.md`, then create the current MVP's technical plan and task specification docs under `docs/`.

This skill does not implement the MVP. It stops at implementation-ready plans and handoff guidance for other agents or humans.

The only allowed outputs are `AGENTS.md`, `docs/mvp-<codename>/technical-plan.md`, per-task docs under `docs/mvp-<codename>/`, and the final Task Phase Handoff Summary.

## Document Language

Before generating `AGENTS.md`, MVP technical plans, task docs, release plans, or emergency release plans, choose one document language for all visible prose:

1. Use the current conversation language.
2. If the conversation language is unclear, use the user's system or environment language.
3. If still unclear, ask the user to choose the document language.

Keep code, commands, paths, package names, API names, config keys, and error messages in their original English form.

## Core Workflow

1. Inspect the repository first: source files, package manager, apps/packages, framework, scripts, lint/format/test/build config, Git branches, `AGENTS.md`, and existing `docs/mvp-*` documents.
2. Decide whether this is a first MVP or a later MVP:
   - Treat an empty/unstarted project as MVP 1 when there is no major source code, or when `AGENTS.md` or MVP docs are missing.
   - For MVP 2 and later, read `AGENTS.md`, the previous MVP technical plan, related docs, code structure, and key implementations before planning.
3. Classify the project as `Web frontend`, `Backend`, `Fullstack`, `Electron`, or `React Native`. If unclear, ask the minimum question needed to classify it.
4. Confirm the current MVP phase codename before creating any MVP docs.
5. For MVP 1 only, perform allowed Git setup when needed: initialize the repository, set `main`, create `develop`, and document branch policy. Do not bootstrap application code.
6. Load `references/mvp-planning-workflow.md`, `references/baseline-stack.md`, and `references/new-repo-questionnaire.md`; confirm technical plan details section by section with the user.
7. Generate or update `AGENTS.md` with project standards, MVP docs index, release plan, emergency release plan, command vocabulary, code style standards, Git workflow, and verification rules.
8. Generate the current MVP technical plan at `docs/mvp-<codename>/technical-plan.md`.
9. Load `references/task-docs-workflow.md`; generate this MVP's module-level task specification docs in the same `docs/mvp-<codename>/` directory.
10. Generate the final Task Phase Handoff Summary, listing task phases and which task docs can run in parallel in each phase, then stop. Do not continue into development execution.

## Defaults

- Language: TypeScript-only with `strict` enabled.
- Workspace: `pnpm` workspaces + Turborepo for new multi-package projects.
- Web frontend: Vite + React; do not default to Next.js.
- Backend: NestJS.
- Fullstack: Vite React + NestJS.
- Desktop: Electron + Vite.
- Mobile: Expo React Native.
- Data: Postgres + Prisma when a database is needed.
- API contract: REST + OpenAPI when frontend and backend communicate.
- UI: Tailwind CSS + shadcn/ui for React surfaces.
- Quality: ESLint + Prettier, with `typecheck`, `lint`, `format:check`, `test`, and `build` as the standard check vocabulary.

## Reference Guide

- `references/mvp-planning-workflow.md`: MVP phase detection, codename series, technical plan questions, and plan template.
- `references/baseline-stack.md`: default stack, project type classification, directories, package boundaries.
- `references/new-repo-questionnaire.md`: concise question sets for Web, Backend, Fullstack, Electron, and React Native projects.
- `references/project-templates.md`: directory templates, scripts, env files, and AGENTS.md outline.
- `references/code-style-baseline.md`: mandatory functional TypeScript style rules.
- `references/project-governance.md`: Git branches, PRs, release, emergency hotfix, and CI governance.
- `references/coding-standards.md`: TypeScript, React, NestJS, Prisma, lint, and formatting standards.
- `references/platform-guides.md`: Vite React, NestJS, Electron, and Expo platform notes.
- `references/testing-ci.md`: unit, integration, E2E, and CI gate guidance.
- `references/task-docs-workflow.md`: per-MVP module task docs generated under `docs/mvp-<codename>/`.

## Hard Rules

- Do not default to Next.js.
- Do not skip repository inspection and project classification.
- Do not write an MVP technical plan before confirming its major sections with the user.
- Do not plan MVP 2+ without reading `AGENTS.md`, the previous MVP technical plan, related docs, and relevant code.
- Do not create an MVP technical plan or task docs until the current MVP phase has a confirmed codename.
- Do not write or modify product source code.
- Do not install dependencies, scaffold apps, run codegen, create migrations, or implement features.
- For MVP 1 only, Git setup may initialize repository metadata and branches, but must not bootstrap application code.
- Generated task docs are implementation specifications, not permission to implement them.
- Do not begin programming after generating the MVP plan.
- Do not execute tasks from the generated task docs.
- The final response must list generated or updated planning documents and task phases with parallelizable tasks.
- If the user wants implementation, require a separate explicit request after the planning output.
- Do not generate task docs outside the current MVP docs directory.
- Do not invent decisions. Put unknowns into `To Confirm`.
- Do not ignore existing repository conventions; record any intentional migration from existing practice.
- When documenting TypeScript code standards, follow `references/code-style-baseline.md` unless a local project standard is stricter.
