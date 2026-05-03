# Testing And CI

Use this reference when documenting AGENTS.md verification commands, task docs, and PR gates for future implementation work.

## Test Layers

- Unit tests: pure functions, reducers, utilities, business rules.
- Component tests: important React UI behavior when valuable.
- API integration tests: Nest controllers/services with test database or mocked adapters.
- E2E tests: critical user workflows with Playwright or the repo's existing tool.

## Default Tools

- Use Vitest for frontend/shared packages unless the repo already uses Jest.
- Use Jest or the NestJS default test setup for backend when the planned or existing stack uses NestJS.
- Use Playwright for browser E2E when Web UI exists.

## CI Gates

Choose planned required gates by project risk. Candidate root commands:

```text
pnpm typecheck
pnpm lint
pnpm format:check
pnpm test
pnpm build
pnpm test:e2e
```

For future `develop -> main` PRs, require verification results in the PR. If a gate is intentionally skipped, record why.

## Acceptance Criteria

Every task document should define:

- Behavior that must work.
- Commands that must pass.
- Manual verification when needed.
- Known risks or deferred checks.
