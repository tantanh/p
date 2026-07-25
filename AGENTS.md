# AGENTS.md

Static site of self-contained AI-model benchmark/pricing dashboards, published via GitHub Pages. No build step.

## Deploy

- `.github/workflows/static.yml` deploys on push to `main`. It uploads the **entire repo root** as the Pages artifact (`path: '.'`), so every committed file at root becomes public live content. Do not commit scratch, draft, or personal files.
- No build, test, or lint command exists. `.kilo/node_modules` is the Kilo plugin runtime, not project dependencies — do not `npm install` to "build".

## Layout

- Root `index.html` — pricing comparison homepage.
- `ai-coding-2026.html` + `ai-coding-2026.md` — paired interactive dashboard and prose ledger for the AI-coding 2026 roster (maintained by hand, no codegen).
- `liquid-glass/index.html` — index for the "liquid glass" demo series; siblings are individual model demos (`liquid-glass-*.html`).
- `liquid-glass-kimi-k3-high.html` — standalone variant at root (not under `liquid-glass/`).
- `archived/index.html` — index for June 2026 AI model reports; siblings are `ai_model_report_june_2026_*.html`. The matching prose ledger for one of them lives at `archived/AI_MODELS_REPORT_*.md` and the standalone report at `archived/ai_model_report.html`.
- `docs/` — supplementary markdown notes (e.g. `ai_model_report.html`).
- Each subfolder has its own `index.html`.

## Page conventions

- Every `.html` is fully self-contained: inline `<style>` and `<script>`, no local CSS/JS assets. The only external resources are Google Fonts. Keep this pattern when editing or adding pages — do not introduce shared asset files.
- Each page defines its own CSS palette (e.g. `--bg`, `--surface`, `--accent`) in `:root`. Match the existing page's palette when editing; there is no global theme.
- Benchmark and pricing data lives inline as JS objects inside the HTML dashboards. Edit data there directly.

## Content sync

- `ai-coding-2026.md` is the prose ledger for `ai-coding-2026.html`. They share the same roster and figures — if you change benchmark/pricing data in one, update the other to keep them in sync, and verify figures against the markdown before relying on them.

## Environment

- `.gitignore` excludes `.playwright-mcp/` (Playwright MCP screenshot output). Keep it ignored.
- `.kilo/kilo.json` mounts a filesystem MCP server scoped to the repo root.
