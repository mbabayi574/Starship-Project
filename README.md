## Starship Admin Dashboard — Agent Quick Guide

Single source of truth for coding agents working on this repo. Keep it short, precise, and actionable.

## What to edit

- Target app: `Migrated Persian Dashboard/` (Vite + React + TypeScript)
- Reference-only (do not modify unless asked):
  - `Legacy Persian Project/` — static Persian HTML/CSS/JS
  - `Modern Project/` — CRA React (English)

Note: Paths contain spaces. Always quote directory names in commands.

## Run commands (pnpm)

```
pnpm -C "Migrated Persian Dashboard" dev       # start dev server
pnpm -C "Migrated Persian Dashboard" build     # type-check + production build
pnpm -C "Migrated Persian Dashboard" preview   # preview built app
pnpm -C "Migrated Persian Dashboard" lint      # run ESLint
```

## Architecture constants (don’t fight these)

- Vite + React + TypeScript; keep `@vitejs/plugin-react-swc` in `vite.config.ts`
- TS configs: `tsconfig.json`, `tsconfig.app.json`, `tsconfig.node.json`
- Entry: `src/main.tsx`, `src/App.tsx`; Global styles: `src/index.css`, `src/App.css`
- Desktop and Persian (RTL) only

## RTL and localization

- Root element must have `dir="rtl"`
- Prefer CSS logical properties over left/right: `margin-inline`, `padding-inline`, `inset-inline`, etc.
- Use fonts with Persian glyphs; ensure `font-display: swap`
- Translate visible strings + aria-labels; keep route paths and component names in English unless specified
- Use Intl APIs for numbers/dates; avoid heavy locale bundles

## Agent guardrails

- Only edit `Migrated Persian Dashboard/`
- Use pnpm; do not switch package managers
- Follow `eslint.config.js`; fix lint errors instead of disabling rules globally
- Quote paths with spaces in all commands
- Performance: prefer code-splitting and lazy-load heavy charts/editors

## Common tasks (quick recipes)

- Add a page/component

  1. Create under `Migrated Persian Dashboard/src/`
  2. Wire to routing or `App.tsx`
  3. Style with CSS/Sass modules or global CSS
  4. Verify RTL layout and semantics

- Port a feature from CRA reference
  1. Inspect in `Modern Project/src/`
  2. Reimplement idiomatically in TS/React for Vite (no CRA-specific wiring)
  3. Replace jQuery patterns with React-first approaches

## Quality gates (before commit/PR)

- Build: `pnpm -C "Migrated Persian Dashboard" build` passes
- Lint: `pnpm -C "Migrated Persian Dashboard" lint` has no errors
- Smoke test dev: app loads, RTL renders correctly, no console errors

## Quick repo map

- `Migrated Persian Dashboard/` — Vite app (edit here)
- `Modern Project/` — CRA reference (English)
- `Legacy Persian Project/` — Static Persian reference

## Goals (context)

- Modernize on Vite, fully Persian RTL, maintain functionality and responsiveness
