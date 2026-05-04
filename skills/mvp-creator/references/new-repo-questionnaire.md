# New Repo Questionnaire

Ask only what cannot be inferred from the repository or user's project description. Keep the first pass concise and choice-required.

Use the native choice tool required by `SKILL.md` whenever it is available. If the native tool does not support multi-select, ask the user to choose the closest option and add missing details in the free-form response.

## Universal Choice Set

Use these choices only when the answer is not already clear.

- Project type: `Web frontend (recommended when the product is browser-only)`, `Backend`, `Fullstack`, `Electron`, `React Native`, `Other / custom`.
- Repository state: `New repo or empty app (recommended when little source exists)`, `Existing repo with conventions to preserve`, `Existing repo with planned migration`, `Other / custom`.
- MVP workflow detail level: `One primary happy-path workflow (recommended for MVP 1)`, `Multiple role-based workflows`, `System/integration workflow`, `Other / custom`.
- First runtime target: `Local development first (recommended for early MVP planning)`, `Cloud deployment first`, `Desktop packaging first`, `Mobile test distribution first`, `Other / custom`.
- Authentication: `No auth for MVP 1 (recommended unless user data or roles exist)`, `Basic user auth`, `Role/permission model`, `External identity provider`, `Other / custom`.
- Data and integrations: `No persistence yet`, `Postgres + Prisma persistence`, `External API integration`, `File storage`, `Jobs/realtime`, `Other / custom`.
- Test and CI gate: `Typecheck + lint + unit tests (recommended baseline)`, `Add integration tests`, `Add E2E tests`, `Minimal checks only`, `Other / custom`.
- Product constraints: `Use default stack and accessible responsive UI (recommended)`, `Existing design system/brand`, `Strict accessibility target`, `Platform-specific constraints`, `Other / custom`.

## Web Frontend

Default: Vite + React + TypeScript + Tailwind + shadcn/ui.

Use these choices for Web-specific confirmations:

- App shape: `SPA-only browser app (recommended default)`, `Static marketing/content site`, `Frontend with separate API/backend`, `Embedded/admin surface`, `Other / custom`.
- Routing: `Simple client routes`, `Nested/protected routes`, `Single-screen workflow`, `Other / custom`.
- Data loading: `Client-side API calls`, `Mock/local data for MVP 1`, `Generated OpenAPI client`, `Other / custom`.
- Forms and validation: `Basic client validation`, `Schema validation with shared types`, `No forms in MVP 1`, `Other / custom`.
- Browser support: `Modern evergreen browsers (recommended)`, `Mobile-first responsive`, `Enterprise/legacy constraints`, `Other / custom`.

## Backend

Default: NestJS + TypeScript.

Use these choices for Backend-specific confirmations:

- Service shape: `REST API (recommended default)`, `Background worker`, `Webhook service`, `Mixed API + worker`, `Other / custom`.
- Persistence: `Postgres + Prisma owned by service`, `No database in MVP 1`, `External system of record`, `Other / custom`.
- Authn/authz: `No auth in MVP 1`, `JWT/session auth`, `Role/permission checks`, `Machine-to-machine auth`, `Other / custom`.
- API contract: `OpenAPI required (recommended for consumers)`, `Internal-only API`, `Webhook contract docs`, `Other / custom`.
- Operations: `Structured logs only`, `Logs + metrics`, `Queues/scheduled jobs`, `File handling`, `Other / custom`.

## Fullstack

Default: Vite React frontend + NestJS backend.

Use these choices for Fullstack-specific confirmations:

- Deployment split: `Separate frontend/backend deployments (recommended default)`, `Unified platform deployment`, `Local-only MVP`, `Other / custom`.
- API boundary: `REST + OpenAPI generated client (recommended)`, `Shared DTO package only`, `Manual API client`, `Other / custom`.
- Shared types: `Dedicated packages/types boundary`, `Backend owns DTOs and exports generated client`, `Keep frontend/backend isolated`, `Other / custom`.
- Auth flow: `No auth for MVP 1`, `Backend session or JWT issued to frontend`, `External identity provider`, `Role-based access`, `Other / custom`.
- Database ownership: `Backend owns Postgres + Prisma`, `No persistence yet`, `External data source`, `Other / custom`.

## Electron

Default: Electron + Vite + TypeScript.

Use these choices for Electron-specific confirmations:

- App mode: `Local-only desktop app (recommended default)`, `Desktop client with remote backend`, `Hybrid local cache + remote sync`, `Other / custom`.
- Process boundary: `Standard main/preload/renderer split`, `Main-process-heavy native integration`, `Renderer-first app with minimal preload`, `Other / custom`.
- Native capabilities: `Filesystem access`, `Native menus/tray`, `Auto-update`, `Signing/notarization`, `Other / custom`.
- Renderer UI: `Vite React renderer (recommended)`, `Existing renderer stack`, `Minimal native shell`, `Other / custom`.
- Distribution: `Development build only for MVP 1`, `Signed macOS build`, `Cross-platform packaged app`, `Other / custom`.

## React Native

Default: Expo React Native + TypeScript.

Use these choices for React Native-specific confirmations:

- Target platform: `iOS and Android (recommended default)`, `iOS first`, `Android first`, `Other / custom`.
- Backend/API ownership: `Use existing/remote API`, `Plan owned backend later`, `Fullstack mobile + owned API now`, `Other / custom`.
- Native capabilities: `None beyond standard app UI`, `Camera/media`, `Push notifications`, `Location/storage/biometrics`, `Other / custom`.
- Offline and persistence: `Online-only MVP`, `Local storage for preferences/cache`, `Offline-first workflow`, `Other / custom`.
- Distribution: `Expo dev build (recommended for early MVP)`, `TestFlight`, `Play Store internal testing`, `Both app stores`, `Other / custom`.
