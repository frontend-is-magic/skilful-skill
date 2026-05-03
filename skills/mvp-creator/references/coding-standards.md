# Coding Standards

Use together with `code-style-baseline.md` when documenting AGENTS.md code standards and task specifications.

## TypeScript

- Enable `strict`.
- Avoid `any`; prefer unknown plus narrowing when input is untrusted.
- Use discriminated unions for state and domain variants.
- Keep DTOs and shared API types in `packages/types` when multiple apps consume them.
- Keep runtime validation at boundaries, not throughout internal pure functions.

## Formatting

Default Prettier baseline:

- 2 spaces.
- Semicolons enabled.
- Single quotes.
- Trailing commas where valid.
- Print width 100.

Document `format` for future write-time formatting and `format:check` for CI.

## ESLint

Default expectations:

- TypeScript-aware linting.
- React rules for React apps.
- Nest/Node rules for backend apps.
- No floating promises.
- No unused variables.
- No parameter reassignment.
- Restricted loop syntax per `code-style-baseline.md`.
- Stable import ordering: builtin, external, workspace, relative.

## React

- Keep components as arrow functions.
- Prefer composition over inheritance and large prop-driven components.
- Keep server/API transformations outside presentational components.
- Avoid redundant state; derive when possible.
- Use accessible shadcn/ui primitives where available.

## NestJS

- NestJS classes are allowed as framework boundaries.
- Keep business rules in pure functions or functional services when practical.
- Controllers translate HTTP inputs/outputs; they should not contain domain logic.
- Use DTO/schema validation at request boundaries.
- Generate OpenAPI for frontend/mobile/desktop clients when relevant.

## Prisma

- Keep schema and migration ownership in `packages/db` for monorepos.
- Do not leak Prisma models as UI view models when API DTOs are needed.
- Encapsulate DB access behind repositories/adapters for non-trivial domains.
