## Starship Admin Dashboard — Copilot Guide

Scope: this repo hosts three artifacts. Edit the Vite app in `Migrated Persian Dashboard/`; use the others as references.

### Targets and boundaries

- Primary app: `Migrated Persian Dashboard/` (Vite + React + TypeScript)
- Reference only: `Modern Project/` (CRA React, English) and `Legacy Persian Project/` (static Persian HTML)
- Paths include spaces — always quote directory names in commands.

### Run and build (pnpm)

```
pnpm -C "Migrated Persian Dashboard" dev       # start dev server
pnpm -C "Migrated Persian Dashboard" build     # type-check + production build
pnpm -C "Migrated Persian Dashboard" preview   # preview built app
pnpm -C "Migrated Persian Dashboard" lint      # ESLint per eslint.config.js
```

### Architecture and conventions (Migrated Persian Dashboard)

- Vite + React 19 + TS; SWC plugin in `vite.config.ts` (keep `@vitejs/plugin-react-swc`).
- Entrypoints: `src/main.tsx` → `src/App.tsx`; global CSS in `src/index.css`, `src/App.css`.
- TS is strict: see `tsconfig.app.json` (noUnusedLocals/Parameters, strict, bundler resolution, verbatimModuleSyntax). Prefix intentional unused with `_`.
- ESM only; no CommonJS imports. JSX runtime is `react-jsx`.
- Static files in `/public` (e.g., `/vite.svg`); imported assets under `src/assets/`.

### RTL and localization (project requirement)

- Ensure root has `dir="rtl"` and verify layouts in RTL. Prefer CSS logical props (`margin-inline`, `inset-inline` …) over left/right.
- Use fonts with Persian glyphs; set `font-display: swap` when adding custom fonts.

### Migration patterns (from references)

- Use `Modern Project/` to study behavior (routing, theming, charts, tables). Reimplement idiomatically in Vite/TS — avoid CRA-specific wiring and jQuery.
- Heavy UI libs in reference: FullCalendar, ApexCharts, DataTables, Quill, Bootstrap. Prefer React wrappers and lazy-load them.
  - Example: `const ApexChart = React.lazy(() => import('react-apexcharts'))` and code-split routes/components.
- Replace imperative DOM toggles (e.g., `slideToggle`, classList mutations) with React state and conditional classes.

### Linting and quality gates

- Follow `eslint.config.js` (typescript-eslint + react-hooks + react-refresh). Fix lint errors instead of disabling rules globally.
- Before commit/PR: build and lint pass; dev smoke-test loads with no console errors and correct RTL rendering.

### File map to know

- `Migrated Persian Dashboard/vite.config.ts` — Vite + SWC plugin.
- `Migrated Persian Dashboard/tsconfig.{app,node}.json` — strict TS and bundler resolution.
- `Migrated Persian Dashboard/src/{main.tsx,App.tsx}` — app bootstrap and root component.
- `Modern Project/src/index.js` — BrowserRouter setup and global styles; use only as behavior reference.

### Notes and gotchas

- If adding routing in Migrated app, install `react-router-dom@^7` and configure in Vite (no CRA tooling).
- Quote paths with spaces in all scripts and shell commands.

If anything above is unclear (e.g., expected RTL baseline, routing strategy, or which reference to follow for a feature), ask for confirmation before implementing.
