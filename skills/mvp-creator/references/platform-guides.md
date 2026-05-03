# Platform Guides

Use the relevant section only.

## Vite React

- Default for Web frontend and Electron renderer.
- Use TypeScript, React, Tailwind, and shadcn/ui.
- Add routing only when the product needs multiple screens.
- Keep API clients and DTOs separate from UI components.
- Prefer environment variables with `VITE_` only for safe public values.

## NestJS

- Default backend stack.
- Use modules/controllers/providers for framework organization.
- Keep domain logic functional and testable outside controllers.
- Expose REST APIs and OpenAPI when frontend/mobile/desktop clients consume them.
- Keep config validation at startup.

## Electron

- Keep main, preload, and renderer boundaries explicit.
- Do not expose broad Node APIs to renderer.
- Renderer follows Vite React rules.
- Confirm packaging, auto-update, signing, native menus, tray, and local storage needs before adding tooling.

## Expo React Native

- Default mobile stack.
- Confirm iOS/Android target, native capabilities, offline needs, and distribution route.
- Keep platform-specific code isolated.
- Share API types and clients with Web/Desktop when possible.
- Avoid assuming browser-only APIs exist.
