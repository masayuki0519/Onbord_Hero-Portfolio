# AI Development Rules

## Source Of Truth

Git and repository files are the source of truth. Do not rely on a single AI conversation history. Important design decisions must be written into `docs/`.

## Required Documentation

When implementing a new system or large behavior change, update related docs when useful:

- `docs/GAME_DESIGN.md`
- `docs/TODO.md`
- `docs/DEV_LOG.md`

## Coding Rules

- Prefer small, scoped changes.
- Do not do broad refactors unless required.
- Preserve existing patterns and naming.
- Keep user-facing Japanese text consistent.
- Avoid changing generated Android or `www` files manually unless the build process requires it.
- Source web files are the root `index.html`, `styles.css`, `app.js`, and assets.
- After web changes, run `npm run cap:sync` before Android builds.

## Verification

For JavaScript changes:

```powershell
node --check app.js
```

For Android sync/build:

```powershell
npm.cmd run cap:sync
cd android
.\gradlew.bat installDebug
```

## Notes For Other AI Agents

- This project uses Capacitor for Android.
- The current package id is `com.onboardhero.game`.
- The app is portrait-oriented.
- Overlay mini-window behavior is implemented in native Android Java under `android/app/src/main/java/com/onboardhero/game/`.
- If Git is unavailable in the shell, ask the user to install Git for Windows or add it to PATH before relying on Git commands.
- The mini-window overlay (`MiniWindowController.java`) is implemented as a
  single static overlay view. Only one instance can ever exist, so "opening
  the mini window auto-closes other mini windows" is already guaranteed by
  this design — no additional close-other-windows logic is needed unless the
  feature is redesigned to support multiple simultaneous overlays.

