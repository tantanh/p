# The Chinese Model Stack

_A working roster for a Claude-based coding agent — built, audited, and superseded in the open, now routing through open-weight Chinese models at a fraction of Opus pricing._

---

## 00 — Premise

This stack exists to answer one question: _can a roster of open-weight Chinese models replace Claude Opus and Sonnet across twelve distinct coding-agent roles_ — and at what cost, with what caveats?

Two rosters are maintained. **Table 1 (Expanded)** keeps three independently-strong models in every fallback column — maximum resilience for autonomous long-horizon runs. **Table 2 (Lean)** collapses to the models that actually fire in practice, trimming carry-weight and token spend where a third fallback was never invoked.

Every benchmark figure below is either **independently reproduced** on standard suites or marked with a glyph (\* vendor-reported, † independently run by Kilo, ‡ vendor-reported pending reproduction). The ledger is the source of truth; the rosters are its interpretation.

---

## 01 — What moved this cycle

_Three decisions, one ledger. Each card maps to a row delta between R04 and R05._

### Δ 01 / PROMOTION — GLM-5.2 enters as a Main

Open-weight (MIT), same price as 5.1, and a real jump: `CODE` Arena #2, Design Arena #1. Terminal-Bench 81.0%. Now owns **Code, Ask, Frontend** outright and takes the Sonnet-fallback column.

### Δ 02 / CONTESTED — Kimi K2.7-Code, held to Alt 1

Vendor MCPMark of 81.1 edges Opus 4.8's 76.4 — but practitioners report the gain **doesn't replicate on real repos**. Lands only in the Expanded _Ask_ column with a contested TS-build flag, pending independent reproduction.

### Δ 03 / VERIFIED — MiniMax M3 earns its seat

Kilo's own audit found **13 of 17 planted TS bugs for $0.07** — tying Opus 4.8 at 18× less cost. Promoted into Table 1 for `REVIEW` `FRONTEND`, displacing the weaker Step 3.7 Flash.

---

## 02 — Roster matrices

_Main fires first; on failure the agent cascades Alt 1 → Alt 2. Expanded keeps three strong hands per column; Lean drops the third where it never fired. Table 3 maps GLM-5.2 reasoning-mode (Max vs High) to each agent._

### Table 1 · Expanded

_12 agents · 3 models per column · maximum resilience for long autonomous runs_

| Agent / Fallback    | Kind            | Main                  | Alt 1                | Alt 2                 |
| ------------------- | --------------- | --------------------- | -------------------- | --------------------- |
| Plan                | strategy        | Kimi K2.6             | MiMo V2.5-Pro        | DeepSeek V4 Pro       |
| Code                | primary write   | GLM-5.2 `NEW`         | Qwen 3.7 Plus        | Hy3                   |
| Ask                 | quick Q&A       | GLM-5.2 `NEW`         | Kimi K2.7-Code `NEW` | DeepSeek V4 Pro       |
| Debug               | fault isolation | Kimi K2.6             | MiMo V2.5-Pro        | DeepSeek V4 Pro       |
| Review              | critique        | MiniMax M3 `VERIFIED` | MiMo V2.5-Pro        | Qwen 3.7 Max          |
| Code Simplifier     | refactor        | Kimi K2.6             | Qwen 3.7 Plus        | Hy3                   |
| Documentation       | prose           | GLM-5.2 `NEW`         | Qwen 3.7 Plus        | Hy3                   |
| Backend Specialist  | server logic    | Kimi K2.6             | MiMo V2.5-Pro        | Hy3                   |
| Frontend Specialist | UI / JSX        | GLM-5.2 `NEW`         | Qwen 3.7 Plus        | MiniMax M3 `VERIFIED` |
| DevOps              | infra / CI      | Kimi K2.6             | Qwen 3.7 Plus        | Hy3                   |
| Opus 4.8 fallback   | tier shadow     | Kimi K2.6             | MiMo V2.5-Pro        | DeepSeek V4 Pro       |
| Sonnet 4.6 fallback | tier shadow     | GLM-5.2 `NEW`         | Qwen 3.7 Plus        | Hy3                   |

### Table 2 · Lean

_12 agents · trimmed third column · lower carry-weight where the Alt 2 never fired_

| Agent / Fallback    | Kind            | Main          | Alt 1         | Alt 2           |
| ------------------- | --------------- | ------------- | ------------- | --------------- |
| Plan                | strategy        | Kimi K2.6     | MiMo V2.5-Pro | DeepSeek V4 Pro |
| Code                | primary write   | GLM-5.2 `NEW` | Qwen 3.7 Plus | Hy3             |
| Ask                 | quick Q&A       | GLM-5.2 `NEW` | Qwen 3.7 Plus | DeepSeek V4 Pro |
| Debug               | fault isolation | Kimi K2.6     | MiMo V2.5-Pro | DeepSeek V4 Pro |
| Review              | critique        | GLM-5.2 `NEW` | MiMo V2.5-Pro | Hy3             |
| Code Simplifier     | refactor        | Kimi K2.6     | Qwen 3.7 Plus | Hy3             |
| Documentation       | prose           | GLM-5.2 `NEW` | Qwen 3.7 Plus | Hy3             |
| Backend Specialist  | server logic    | Kimi K2.6     | MiMo V2.5-Pro | Hy3             |
| Frontend Specialist | UI / JSX        | GLM-5.2 `NEW` | Qwen 3.7 Plus | Hy3             |
| DevOps              | infra / CI      | Kimi K2.6     | Qwen 3.7 Plus | Hy3             |
| Opus 4.8 fallback   | tier shadow     | Kimi K2.6     | MiMo V2.5-Pro | DeepSeek V4 Pro |
| Sonnet 4.6 fallback | tier shadow     | GLM-5.2 `NEW` | Qwen 3.7 Plus | Hy3             |

### Table 3 · GLM-5.2 Modes

_11 GLM-5.2 agents · 6 Max / 5 High · Code Simplifier runs on Kimi K2.6_

| Agent               | Kind            | GLM-5.2 Mode        | Rationale                                                                                                                                                                                                                                                                        |
| ------------------- | --------------- | ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Plan                | strategy        | **Max**             | Architectural decisions — named directly as a Max use case                                                                                                                                                                                                                       |
| Code                | primary write   | **High**            | Everyday generation against a clear spec                                                                                                                                                                                                                                         |
| Ask                 | quick Q&A       | **High**            | Direct Q&A, no benefit from extra deliberation                                                                                                                                                                                                                                   |
| Debug               | fault isolation | **Max**             | "Intricate debugging" — named directly as a Max use case                                                                                                                                                                                                                         |
| Review              | critique        | **Max**             | Catching subtle bugs is exactly where deeper reasoning pays off                                                                                                                                                                                                                  |
| Code Simplifier     | refactor        | **N/A — Kimi K2.6** | Refactoring is disciplined execution within constraints, not open-ended judgment — Kimi's 4000+ tool-call endurance and vision still matter here. However, "complex refactors" is explicitly Max-mode territory — if ever routed through GLM-5.2, Max would be the right setting |
| Documentation       | prose           | **High**            | Prose generation is a "fairly direct" task                                                                                                                                                                                                                                       |
| Backend Specialist  | server logic    | **Max**             | Schema / auth / licensing trade-offs — architectural judgment                                                                                                                                                                                                                    |
| Frontend Specialist | UI / JSX        | **High**            | Pattern-based UI implementation                                                                                                                                                                                                                                                  |
| DevOps              | infra / CI      | **High**            | Bounded, structured tasks — escalate to Max only for complex pipeline redesign                                                                                                                                                                                                   |
| Opus 4.8 fallback   | tier shadow     | **Max**             | Highest-stakes moments — use the deeper mode                                                                                                                                                                                                                                     |
| Sonnet 4.6 fallback | tier shadow     | **High**            | Sonnet-tier work is volume / speed-oriented by design                                                                                                                                                                                                                            |

### Table 4 — Claude tier per agent

**Opus 4.8** — Judgment-heavy

| Agent              | Kind            | Rationale                                                                                             |
| ------------------ | --------------- | ----------------------------------------------------------------------------------------------------- |
| Plan               | strategy        | Architecture decisions are exactly where the Kilo test showed models diverge most — worth the premium |
| Debug              | fault isolation | Diagnosing root cause is a judgment task, same family as Plan                                         |
| Review             | critique        | 4× lower code flaw miss rate vs 4.7 matters most where review quality is the entire point             |
| Backend Specialist | server logic    | Schema/auth/licensing trade-offs are judgment calls with long-term cost if wrong                      |

**Sonnet 4.6** — Execution-heavy

| Agent               | Kind          | Rationale                                                                       |
| ------------------- | ------------- | ------------------------------------------------------------------------------- |
| Code                | primary write | Routine generation against a clear spec; Sonnet's 1M context and lower cost fit |
| Ask                 | quick Q&A     | Lightweight Q&A, no frontier reasoning needed                                   |
| Code Simplifier     | refactor      | Refactoring within existing constraints, not open-ended judgment                |
| Documentation       | prose         | Prose generation, well within Sonnet's range, cost-conscious                    |
| Frontend Specialist | UI / JSX      | Pattern-based UI implementation, mechanical relative to backend decisions       |
| DevOps              | infra / CI    | Structured, bounded tasks (Dockerfiles, CI YAML)                                |

---

## 03 — Full ledger

_The source of truth. Scores colour-graded by tier; glyphs flag provenance._

**Score tiers:** Green ≥58% Pro / ≥80% Verified / ≥70% Terminal · Blue 50–57% / 75–79% / 60–69% · Amber 40–49% / 70–74% / 50–59% · Red <40% / <70% / <50%

### Claude — Opus tier

| Model           | Role     | TS build | SWE-bench Pro | SWE-bench Verified | Terminal-Bench | Context | Vision | Open weights | Input $/1M | Output $/1M | Key note                                                     |
| --------------- | -------- | -------- | ------------- | ------------------ | -------------- | ------- | ------ | ------------ | ---------- | ----------- | ------------------------------------------------------------ |
| Claude Opus 4.8 | Opus     | Pass     | 69.2%         | 88.6%              | 74.6–85%       | 200K    | Yes    | —            | $5.00      | $25.00      | Now the fallback target. 4× lower code-flaw miss rate vs 4.7 |
| Claude Opus 4.7 | Replaced | Pass     | 64.3%         | 87.6%              | 66.1%          | 200K    | Yes    | —            | $5.00      | $25.00      | Superseded by Opus 4.8 in this session                       |
| Claude Opus 4.6 | Legacy   | Pass     | 53.4%         | 80.8%              | —              | 200K    | Yes    | —            | $5.00      | $25.00      | Original baseline this stack was designed around             |

### Claude — Sonnet tier

| Model             | Role   | TS build | SWE-bench Pro | SWE-bench Verified | Terminal-Bench | Context | Vision | Open weights | Input $/1M | Output $/1M | Key note                                        |
| ----------------- | ------ | -------- | ------------- | ------------------ | -------------- | ------- | ------ | ------------ | ---------- | ----------- | ----------------------------------------------- |
| Claude Sonnet 4.6 | Sonnet | Pass     | —             | 79.6%              | 59.1%          | 1M      | Yes    | —            | $3.00      | $15.00      | 70% fewer tokens vs Sonnet 4.5 in agentic loops |
| Claude Sonnet 4.5 | Legacy | Pass     | 45.9%         | 77.2%              | 50.0%          | 200K    | Yes    | —            | $3.00      | $15.00      | 30hr+ autonomous runs confirmed                 |

### Roster — Main models

| Model         | Role       | TS build | SWE-bench Pro | SWE-bench Verified | Terminal-Bench | Context | Vision | Open weights | Input $/1M | Output $/1M | Key note                                                                     |
| ------------- | ---------- | -------- | ------------- | ------------------ | -------------- | ------- | ------ | ------------ | ---------- | ----------- | ---------------------------------------------------------------------------- |
| Kimi K2.6     | Main       | Pass     | 58.6%         | 80.2%              | 66.7%          | 256K    | Yes    | —            | $0.60      | $2.50       | 4000+ tool calls / 13hr stability. GPQA-Diamond 90.5                         |
| GLM-5.2 `NEW` | Main       | Pass     | 62.1%         | —                  | 81.0%          | 1M      | —      | Yes (MIT)    | $1.40      | $4.40       | Code Arena #2 (independent), Design Arena #1. Same price as 5.1, big upgrade |
| GLM-5.1       | Replaced   | Pass     | 58.4%         | ~78%               | 62.0%          | 200K    | —      | Yes (MIT)    | $1.40      | $4.40       | Superseded by GLM-5.2 in this session                                        |
| Qwen 3.7 Max  | Alt 2 (v1) | Pass     | 60.6%         | 80.4%              | 69.7%          | 1M      | No     | —            | $2.50      | $7.50       | Text-only. Now second-highest SWE-bench Pro behind GLM-5.2                   |

### Roster — Alt 1 models

| Model                | Role         | TS build   | SWE-bench Pro | SWE-bench Verified | Terminal-Bench | Context | Vision | Open weights   | Input $/1M | Output $/1M | Key note                                                                                                                                       |
| -------------------- | ------------ | ---------- | ------------- | ------------------ | -------------- | ------- | ------ | -------------- | ---------- | ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| MiMo V2.5-Pro        | Alt 1        | Pass       | 57.2%         | 78.9%              | 68.4%\*        | 1M\*    | Yes    | Yes            | $1.00      | $3.00       | 1M ctx = 4× price uplift ($4/$12). \*Vendor Terminal-Bench                                                                                     |
| Qwen 3.7 Plus        | Alt 1        | Builds\*   | —             | 78.8%              | 70.3%          | 1M      | Yes    | —              | $0.40      | $1.60       | \*Builds, less idiomatic JSX. ScreenSpot Pro 79%                                                                                               |
| Kimi K2.7-Code `NEW` | Alt 1 (v1)   | Contested  | —‡            | —‡                 | —‡             | 256K    | Yes    | Yes (Mod. MIT) | $1.14      | $4.80       | ‡Vendor-only (MCPMark 81.1 vs Opus 4.8's 76.4). Practitioners report gains don't replicate on real repos. 30% fewer reasoning tokens than K2.6 |
| DeepSeek V4 Flash    | Demoted (v1) | Unverified | —             | 79.0%              | —              | 1M      | —      | Yes            | $0.14      | $0.28       | Cheapest in table. Replaced by Kimi K2.7-Code for Ask this round                                                                               |

### Roster — Alt 2 models

| Model                 | Role         | TS build | SWE-bench Pro | SWE-bench Verified | Terminal-Bench | Context | Vision | Open weights     | Input $/1M | Output $/1M | Key note                                                                                                                      |
| --------------------- | ------------ | -------- | ------------- | ------------------ | -------------- | ------- | ------ | ---------------- | ---------- | ----------- | ----------------------------------------------------------------------------------------------------------------------------- |
| DeepSeek V4 Pro       | Alt 2        | Failed   | ~55%          | 80.6%              | 44.0%          | 1M      | —      | Yes              | $0.435     | $0.87       | TS build failed in Kilo's own test. Reasoning-only agents only                                                                |
| Hy3 (Hunyuan 3)       | Alt 2        | Pass     | —             | 74.4%              | 54.4%          | 256K    | —      | Yes              | ~$0.17     | Free\*      | \*Free in Kilo Code currently. 99.99% production uptime                                                                       |
| MiniMax M3 `VERIFIED` | Main         | Pass†    | 59.0%‡        | —                  | 66.0%‡         | 1M      | Yes    | Yes              | $0.30      | $1.20       | †Kilo's own audit: found 13/17 planted TS bugs for $0.07, tying Opus 4.8 at 18× less cost. Now in Table 1 for Review/Frontend |
| Step 3.7 Flash        | Demoted (v1) | Untested | 56.3%         | 76.5%‡             | 59.5%          | 256K    | Yes    | Yes (Apache 2.0) | $0.20      | $1.15       | Replaced by MiniMax M3 — weaker, less recent verification                                                                     |

### Watchlist — not in roster

| Model            | Role      | TS build | SWE-bench Pro | SWE-bench Verified | Terminal-Bench | Context | Vision | Open weights | Input $/1M | Output $/1M | Key note                                                                       |
| ---------------- | --------- | -------- | ------------- | ------------------ | -------------- | ------- | ------ | ------------ | ---------- | ----------- | ------------------------------------------------------------------------------ |
| Nemotron 3 Super | Not a fit | Untested | —             | 60.5%              | —              | 128K    | —      | Yes (NVIDIA) | Self-host  | Self-host   | Best US open-weight model. Still trails the Chinese stack here on every metric |

---

## 04 — How to read this

| Colour | Tier     | SWE-bench Pro | SWE-bench Verified | Terminal-Bench |
| ------ | -------- | ------------- | ------------------ | -------------- |
| Green  | Top tier | ≥58%          | ≥80%               | ≥70%           |
| Blue   | Strong   | 50–57%        | 75–79%             | 60–69%         |
| Amber  | Adequate | 40–49%        | 70–74%             | 50–59%         |
| Red    | Limited  | <40%          | <70%               | <50%           |
| —      | No data  | benchmark N/A | —                  | —              |

**Glyph key:**

- `*` = vendor-reported only
- `†` = independently run by Kilo
- `‡` = vendor-reported, pending independent reproduction on standard suites

**TS build** statuses: Pass / Builds / Contested / Unverified / Failed / Untested

---

_Merged · AI_MODELS_REPORT.md × ai_model_report.html · R05 · June 2026 · internal_

_Created with GLM-5.2 High_
