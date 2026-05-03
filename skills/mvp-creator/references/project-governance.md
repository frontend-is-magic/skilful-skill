# Project Governance

Use this reference when documenting Git, PR, commit, release, emergency release, and branch policy in planning artifacts.

## Branch Model

- The first planning and Git setup commit may be made directly on `main`.
- After initial planning and Git setup, `main` is the stable branch and should not be used for daily development.
- Use `develop` as the integration branch.
- Use `feat/xxx` for regular feature work and merge into `develop`.
- Small changes may be merged locally into `develop` when risk is low and scope is clear.
- Future larger features, risky changes, cross-module work, and release candidates should use PR review.
- Final release flow: open PR from `develop` to `main`.

## Merge Strategy

- Default PR merge strategy: Squash merge.
- A merged PR should produce one coherent commit on the target branch.
- Delete feature branches after merge unless they are long-lived coordination branches.

## Commit Convention

Use Conventional Commits:

- `feat:`
- `fix:`
- `chore:`
- `refactor:`
- `test:`
- `docs:`
- `style:`
- `build:`
- `ci:`

Use scopes when useful: `feat(api): add session endpoint`.

## Branch Protection

- Protect `main` strictly.
- Keep `develop` flexible for integration efficiency unless the project risk requires stricter protection.
- Required checks for `main` are selected by project risk from: `typecheck`, `lint`, `format:check`, `test`, `build`, `test:e2e`.

## PR Requirements

For `develop -> main` PRs, include:

- Change summary.
- Verification results.
- Risks, rollout notes, or rollback plan.
- Linked issue/task when one exists.

Feature PRs into `develop` may use a lighter description, but should still state what changed and how it was checked. Record this as future implementation guidance only.

## MVP Release Plan

Every MVP technical plan and `AGENTS.md` release section should include a future execution checklist:

- Source and target branches.
- Required checks selected by project risk.
- Target environment.
- Data migration or seed steps.
- Deployment steps.
- Post-release verification.
- Rollback entrypoint.
- Documentation updates.

Normal release flow: PR from `develop` to `main`.

## Emergency Release Plan

Default hotfix flow:

1. Branch from `main` as `hotfix/xxx`.
2. Apply the smallest safe fix in the implementation phase.
3. Run required verification for the affected scope in the implementation phase.
4. PR back to `main`.
5. Release from `main`.
6. Sync the fix back to `develop`.
7. Update affected MVP docs, release notes, and any follow-up tasks.

If the project is not yet production-facing, the user may choose a lighter emergency flow, but record that decision in `AGENTS.md`.

## Versioning And Releases

- For libraries and multi-package publishable workspaces, consider Changesets.
- For ordinary app projects, git tags and release notes are enough by default.
- Do not add release tooling until the project actually needs package publishing or automated changelog/version management.
