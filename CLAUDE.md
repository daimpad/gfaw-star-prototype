# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

This repo contains **only a pre-built, static output artifact**: a single self-contained `index.html` (~230KB, minified React app bundled by Vite) that serves as a clickable UI mockup of the "STAR" sustainability tool frontend. There is no source code, no `package.json`, and no build tooling here — the entire app (JS + CSS) is inlined into `index.html` so it opens directly via `file://` with no server, no install step, and no dependencies. All data in the mockup is mocked; there is no backend and no real data.

Because there is nothing to compile, lint, or test in this repo, there are no build/lint/test commands to run here. Do not attempt to `npm install` or add tooling to this repo — it is intentionally just the built output.

## Where the actual source lives

The real source code is in a **separate, sibling repository/directory called `cse-star-app/`**, which is not part of this repo. Per `README.md`, updating the mockup means building it there and copying the output in:

```bash
cd cse-star-app
npm run build:prototype
cp dist/index.html ../prototype/index.html
```

If asked to change actual application behavior (not just the static artifact), that work belongs in `cse-star-app/`, not here — check whether that repository is available/added to the session before assuming changes can be made in-place. Editing the minified `index.html` directly by hand is not viable for real feature work; it should only be treated as a build output to be replaced wholesale.

## Deployment

`.github/workflows/static.yml` deploys the repository root as-is to GitHub Pages on every push to `main` (or manually via `workflow_dispatch`). It uploads the entire repo directory (`path: '.'`) and publishes it — so `index.html` is served directly with no build step in CI. Pushing an updated `index.html` to `main` is the entire release process for this mockup.

## Mockup feature scope (for context when reviewing/discussing the UI)

Per `README.md`, the prototype covers: login/role selection (Kunde/Auditor/Admin), an overview/dashboard, STAR form-filling (live star rating visualization, progress state, local mock AI suggestions), report import (CSRD/VSME) with mapping suggestions, a star chart (6 real CSE categories with sliders), an audit flow (5 ratings, 3 verification methods, deviation banners, completion flow), controlling/CO₂ mock charts, a report preview, and a company profile section (company type + FTE count).
