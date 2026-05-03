# Code Style Baseline

Use this reference for TypeScript implementation, review, and AGENTS.md code style sections.

## Core Rule

Write declarative functional TypeScript. Business logic defaults to pure functions, immutable data, typed outcomes, and function composition. Imperative flow and OOP are exceptions, not defaults.

## Mandatory Rules

- Use arrow functions. Avoid `function` declarations and expressions unless a framework or third-party API requires `this`, hoisting, overload declarations, or a specific function shape.
- Avoid OOP in business logic. `class` is allowed for NestJS decorators/providers/controllers, Error classes, ORM/framework adapters, and external interoperability.
- Do not use `for`, `while`, or `for...of` by default. Use `map`, `filter`, `reduce`, `flatMap`, `some`, `every`, `find`, `Object.keys`, `Object.values`, and `Object.entries`.
- Do not mutate inputs or shared state. Avoid `push`, `splice`, in-place `sort`, property reassignment on existing objects, and parameter reassignment.
- Prefer immutable updates: spread, `toSorted`, `toSpliced`, `with`, object reconstruction, and reducer-style transitions.
- Use guard clauses and expression-oriented branching. Avoid deep nested `if`/`else` and large `switch` blocks; prefer maps, discriminated unions, and extracted functions.
- Use TypeScript `type`/`interface` for internal modeling. Use runtime schemas at boundaries: env, HTTP, forms, external APIs, files, and webhooks.
- Use a lightweight project-local `Result` helper for expected business failures.
- Use `Promise.all`, `Promise.allSettled`, async mapping, and task composition for independent async work. Avoid serial `await` inside loops.
- Keep side effects at boundaries: controllers, adapters, repositories, event handlers, and platform integrations.

## Result Shape

Use a small helper in `packages/utils` unless the project already has one:

```ts
export type Result<T, E = Error> =
  | { readonly ok: true; readonly value: T }
  | { readonly ok: false; readonly error: E };

export const ok = <T>(value: T): Result<T, never> => ({ ok: true, value });

export const err = <E>(error: E): Result<never, E> => ({ ok: false, error });
```

Use `Result` for expected failures: validation outcomes, business rule rejection, not found, permission denial. Throw only for unexpected defects or framework boundary handling.

## React State

- Prefer derived data over duplicated state.
- Use immutable state updates.
- Use reducer actions for complex flows.
- Keep API transformation and domain calculation outside components where practical.

## ESLint Enforcement

Automate rules where practical:

- Prefer arrow callbacks/functions.
- Disallow parameter reassignment.
- Disallow restricted syntax: `ForStatement`, `WhileStatement`, `ForOfStatement`.
- Disallow unused variables and floating promises.
- Enforce import ordering.

Use review checklist for rules that are hard to automate: pure boundaries, meaningful Result usage, overuse of classes, and hidden mutation.

## Exceptions

Allowed exceptions:

- Framework requirements.
- Performance hotspots proven by measurement.
- Third-party API interoperability.
- Low-level adapter code.

Add a short local comment explaining the reason. Do not use exceptions as a style preference.
