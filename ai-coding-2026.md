# The Chinese Model Stack

_A working roster for a Claude-based coding agent — built, audited, and superseded in the open, now routing through open-weight Chinese models at a fraction of Opus pricing. R09 makes Claude Opus 5 the fallback target and adds Gemini 2.5 Flash to the comparison ledger._

---

## 00 — Premise

This stack exists to answer one question: _can a roster of open-weight Chinese models replace Claude Opus and Sonnet across twelve distinct coding-agent roles_ — and at what cost, with what caveats?

Three open-model rosters are maintained. **Table 1 (Expanded)** keeps three independently-strong models in every fallback column. **Table 2 (Lean)** trims carry-weight where a third fallback rarely fires. **Table 5 (Grok 4.5)** is Lean-shaped, with Grok routed by agent fit. Table 3 records GLM-5.2 effort and Table 4 maps Claude tiers.

Every benchmark figure below is either **independently reproduced** on a named suite or marked with a glyph (\* vendor-reported, † pricing qualifier, ‡ vendor-reported pending reproduction). Terminal-Bench 2.0 and 2.1 are labeled explicitly because their scores are not interchangeable. The ledger is the source of truth; the rosters are its interpretation. It tracks **27 models** across five tables.

---

## 01 — What moved this cycle

_Six decisions, one ledger. Each item maps to a row delta between R08 and R09._

### Δ 01 / NEW BASELINE

Claude Opus 5, released July 24, is now the current Opus fallback target at $5/$25. Anthropic has not yet published comparable SWE-bench Pro, SWE-bench Verified, or verified Terminal-Bench 2.1 results, so those cells remain blank rather than borrowing scores from another suite.

### Δ 02 / MODEL IDENTITY

The requested “Agnes 2.5 Flash” does not exist in OpenRouter, Hugging Face, or benchmark catalogs. It was confirmed as **Google Gemini 2.5 Flash**: a closed, multimodal 1M-context model at $0.30/$2.50.

### Δ 03 / SUITE NORMALIZATION

Independent Terminal-Bench 2.1 results replace mixed or ambiguous values: Fable 5 83.8%, Grok 4.5 79.3%, and Sonnet 5 74.6%. Kimi K2.6/K3 values remain explicitly labeled Terminal-Bench 2.0 vendor runs.

### Δ 04 / KIMI K3 CORRECTION

Kimi K3 is corrected to SWE-bench Pro 63.4%\*, Terminal-Bench 2.0 71.8%\*, 1M context, and official API pricing of $3 cache-miss input / $15 output (cache-hit input $0.30).

### Δ 05 / PRICING CORRECTION

Kimi K2.6 is corrected to $0.95 cache-miss input / $4 output ($0.16 cache hit). Kimi K2.7-Code is corrected to $0.95/$4 ($0.19 cache hit). Sonnet 5 shows its live $2/$10 introductory rate through August 31.

### Δ 06 / PROVENANCE AUDIT

Scores without a reproducible primary or independent source remain visibly marked vendor-only or blank. No missing score is inferred from a neighboring model, harness, or benchmark version.

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
| Debug               | fault isolation | Kimi K3 `NEW`         | Kimi K2.6            | MiMo V2.5-Pro          |
| Review              | critique        | MiniMax M3 `VERIFIED` | MiMo V2.5-Pro        | Qwen 3.7 Max          |
| Code Simplifier     | refactor        | Kimi K3 `NEW`         | Kimi K2.6            | Qwen 3.7 Plus         |
| Documentation       | prose           | GLM-5.2 `NEW`         | Qwen 3.7 Plus        | Hy3                   |
| Backend Specialist  | server logic    | Kimi K3 `NEW`         | Kimi K2.6            | MiMo V2.5-Pro          |
| Frontend Specialist | UI / JSX        | GLM-5.2 `NEW`         | Qwen 3.7 Plus        | MiniMax M3 `VERIFIED` |
| DevOps              | infra / CI      | Kimi K3 `NEW`         | Kimi K2.6            | Qwen 3.7 Plus         |
| Opus 5 fallback     | tier shadow     | Kimi K2.6             | MiMo V2.5-Pro        | DeepSeek V4 Pro       |
| Sonnet 5 fallback   | tier shadow     | GLM-5.2 `NEW`         | Qwen 3.7 Plus        | Hy3                   |

### Table 2 · Lean

_12 agents · trimmed third column · lower carry-weight where the Alt 2 never fired_

| Agent / Fallback    | Kind            | Main          | Alt 1         | Alt 2           |
| ------------------- | --------------- | ------------- | ------------- | --------------- |
| Plan                | strategy        | Kimi K2.6     | MiMo V2.5-Pro | DeepSeek V4 Pro |
| Code                | primary write   | GLM-5.2 `NEW` | Qwen 3.7 Plus | Hy3             |
| Ask                 | quick Q&A       | GLM-5.2 `NEW` | Qwen 3.7 Plus | DeepSeek V4 Pro |
| Debug               | fault isolation | Kimi K3 `NEW` | Kimi K2.6     | MiMo V2.5-Pro   |
| Review              | critique        | GLM-5.2 `NEW` | MiMo V2.5-Pro | Hy3             |
| Code Simplifier     | refactor        | Kimi K3 `NEW` | Kimi K2.6     | Qwen 3.7 Plus   |
| Documentation       | prose           | GLM-5.2 `NEW` | Qwen 3.7 Plus | Hy3             |
| Backend Specialist  | server logic    | Kimi K3 `NEW` | Kimi K2.6     | MiMo V2.5-Pro   |
| Frontend Specialist | UI / JSX        | GLM-5.2 `NEW` | Qwen 3.7 Plus | Hy3             |
| DevOps              | infra / CI      | Kimi K3 `NEW` | Kimi K2.6     | Qwen 3.7 Plus   |
| Opus 5 fallback     | tier shadow     | Kimi K2.6     | MiMo V2.5-Pro | DeepSeek V4 Pro |
| Sonnet 5 fallback   | tier shadow     | GLM-5.2 `NEW` | Qwen 3.7 Plus | Hy3             |

### Table 3 · GLM-5.2 Modes

_11 GLM-5.2 agents · 6 Max / 5 High · Code Simplifier runs on Kimi K3_

| Agent               | Kind            | GLM-5.2 Mode        | Rationale                                                                                                |
| ------------------- | --------------- | ------------------- | -------------------------------------------------------------------------------------------------------- |
| Plan                | strategy        | **Max**             | Architectural decisions — named directly as a Max use case                                               |
| Code                | primary write   | **High**            | Everyday generation against a clear spec                                                                   |
| Ask                 | quick Q&A       | **High**            | Direct Q&A, no benefit from extra deliberation                                                             |
| Debug               | fault isolation | **Max**             | "Intricate debugging" — named directly as a Max use case                                                   |
| Review              | critique        | **Max**             | Catching subtle bugs is exactly where deeper reasoning pays off                                             |
| Code Simplifier     | refactor        | **N/A — Kimi K3**   | Refactoring is disciplined execution within constraints, not open-ended judgment                            |
| Documentation       | prose           | **High**            | Prose generation is a "fairly direct" task                                                               |
| Backend Specialist  | server logic    | **Max**             | Schema / auth / licensing trade-offs — architectural judgment                                                |
| Frontend Specialist | UI / JSX        | **High**            | Pattern-based UI implementation                                                                            |
| DevOps              | infra / CI      | **High**            | Bounded, structured tasks — escalate to Max only for complex pipeline redesign                              |
| Opus 5 fallback     | tier shadow     | **Max**             | Highest-stakes moments — use the deeper mode                                                                 |
| Sonnet 5 fallback   | tier shadow     | **High**            | Sonnet-tier work is volume / speed-oriented by design                                                     |

### Table 4 — Claude tier per agent

**Opus 5** — Judgment-heavy

| Agent              | Kind            | Effort | Rationale                                                                                                  |
| ------------------ | --------------- | ------ | ---------------------------------------------------------------------------------------------------------- |
| Plan               | strategy        | Xhigh  | Architectural judgment and highest-stakes planning                                                            |
| Debug              | fault isolation | Xhigh  | Root-cause diagnosis is judgment work                                                                          |
| Review             | critique        | Xhigh  | Catching subtle flaws is where the Opus tier earns its cost                                                    |
| Backend Specialist | server logic    | Xhigh  | Schema/auth/licensing trade-offs carry long-term cost if wrong                                                |

**Sonnet 5** — Execution-heavy

| Agent               | Kind          | Effort  | Rationale                                                                                            |
| ------------------- | ------------- | ------- | ---------------------------------------------------------------------------------------------------- |
| Code                | primary write | Medium  | Anthropic states medium now matches what used to require Sonnet 4.6 at high — same quality, lower cost |
| Ask                 | quick Q&A     | Low     | Lightweight Q&A, no frontier reasoning needed                                                            |
| Code Simplifier     | refactor      | Medium  | Refactoring within known constraints, not open-ended judgment                                            |
| Documentation       | prose         | Low     | Prose generation, well within Sonnet's range, cost-conscious                                           |
| Frontend Specialist | UI / JSX      | Medium  | Pattern-based UI implementation                                                                          |
| DevOps              | infra / CI    | Medium  | Structured, bounded tasks; escalate to Xhigh only for complex pipeline redesigns                        |

### Table 5 · Grok 4.5

_12 agents · Lean shape · Grok Main on seven judgment/terminal-heavy agents and Alt 1 on five execution-heavy agents_

| Agent | Kind | Main | Alt 1 | Alt 2 |
| --- | --- | --- | --- | --- |
| Plan | strategy | Grok 4.5 | Kimi K2.6 | MiMo V2.5-Pro |
| Code | primary write | Grok 4.5 | Kimi K3 | Qwen 3.7 Plus |
| Ask | quick Q&A | GLM-5.2 | Grok 4.5 | Qwen 3.7 Plus |
| Debug | fault isolation | Grok 4.5 | Kimi K3 | MiMo V2.5-Pro |
| Review | critique | Grok 4.5 | GLM-5.2 | MiMo V2.5-Pro |
| Code Simplifier | refactor | Kimi K3 | Grok 4.5 | Qwen 3.7 Plus |
| Documentation | prose | GLM-5.2 | Grok 4.5 | Qwen 3.7 Plus |
| Backend Specialist | server logic | Grok 4.5 | Kimi K3 | MiMo V2.5-Pro |
| Frontend Specialist | UI / JSX | GLM-5.2 | Grok 4.5 | Qwen 3.7 Plus |
| DevOps | infra / CI | Grok 4.5 | Kimi K3 | Qwen 3.7 Plus |
| Opus 5 fallback | tier shadow | Grok 4.5 | Kimi K3 | MiMo V2.5-Pro |
| Sonnet 5 fallback | tier shadow | GLM-5.2 | Grok 4.5 | Qwen 3.7 Plus |

---

## 03 — Full ledger

_The source of truth. Scores colour-graded by tier; glyphs flag provenance. Hover any row to focus._

**Score tiers:** Green ≥58% Pro / ≥80% Verified / ≥70% Terminal · Blue 50–57% / 75–79% / 60–69% · Amber 40–49% / 70–74% / 50–59% · Red <40% / <70% / <50%

### Claude — Opus tier

| Model            | Role  | TS build | SWE-bench Pro | SWE-bench Verified | Terminal-Bench | Context | Vision | Open weights | Key note                                         |
| ---------------- | ----- | -------- | ------------- | ------------------ | -------------- | ------- | ------ | ------------ | ---------------------------------------------- |
| Claude Opus 5 `NEW` | Opus | Untested | —            | —                  | —              | 1M      | Yes    | —            | Current Opus fallback target; comparable public scores not yet available |
| Claude Fable 5 `NEW` | Opus | Pass | 80.0%         | 95.0%              | 83.8% (2.1)   | 1M      | Yes    | —            | Independent TB 2.1 via Claude Code, xhigh |
| Claude Mythos Preview | Opus | Pass | 77.8%         | 93.9%              | —              | 1M      | Yes    | —            | Preview-only; superseded by restricted-access Mythos 5 |

### Claude — Sonnet tier

| Model               | Role    | TS build | SWE-bench Pro | SWE-bench Verified | Terminal-Bench | Context | Vision | Open weights | Key note                                            |
| ------------------- | ------- | -------- | ------------- | ------------------ | -------------- | ------- | ------ | ------------ | --------------------------------------------------- |
| Claude Sonnet 5 `NEW` | Sonnet  | Pass     | 63.2%         | 85.2%              | 74.6% (2.1)   | 1M      | Yes    | —            | Intro price through Aug 31 then price increases. Independent TB 2.1 |
| Claude Sonnet 4.6     | Replaced | Pass    | 61.4%         | 79.6%              | 59.1%          | 200K    | Yes    | —            | Superseded by Sonnet 5                                  |

### Roster — Main models

| Model       | Role  | TS build | SWE-bench Pro | SWE-bench Verified | Terminal-Bench | Context | Vision | Open weights | Key note                                                              |
| ----------- | ----- | -------- | ------------- | ------------------ | -------------- | ------- | ------ | ------------ | ------------------------------------------------------------------- |
| Pass     | 58.6%         | 80.2%              | 66.7%* (2.0)   | 262K    | Yes    | —            | Vendor TB 2.0; cache-miss input pricing, cache hit discounted                    
| Pass    | 63.4%*        | —                  | 71.8%* (2.0)   | 1M      | Yes    | —            | Vendor max-effort scores; cache-miss input pricing, cache hit discounted               
| Pass   | 62.1%         | 80.4%              | 81.0%* (2.1)   | 1M      | No     | Yes (MIT)    | Vendor TB 2.1; no independent leaderboard submission               
| Pass  | 58.4%         | ~78%               | 58.7% (2.1)    | 200K    | No     | Yes (MIT)    | Independent TB 2.1 via Claude Code, max                             
| Pass | 60.6%         | 80.4%              | 69.7%          | 1M      | No     | —            | Text-only. Now second-highest SWE-bench Pro behind GLM-5.2             

### Roster — Alt 1 models

| Model                 | Role        | TS build  | SWE-bench Pro | SWE-bench Verified | Terminal-Bench | Context | Vision | Open weights    | Key note                                             |
| --------------------- | ----------- | --------- | ------------- | ------------------ | -------------- | ------- | ------ | --------------- | ---------------------------------------------------- |
| MiMo V2.5-Pro         | Alt 1       | Pass      | 57.2%         | 78.9%              | 68.4%*         | 1M*     | Yes    | Yes             | 1M ctx = 4× price uplift ($4/$12). *Vendor Terminal-Bench 
| Qwen 3.7 Plus         | Alt 1       | Builds*   | —             | 77.7%              | 70.3%          | 1M      | Yes    | —               | *Builds, less idiomatic JSX. ScreenSpot Pro 79%        
| Kimi K2.7-Code `NEW`  | Alt 1 (v1)  | Contested | —‡            | —‡                 | —‡             | 256K    | Yes    | Yes (Mod. MIT)  | ‡Vendor-only MCPMark; †cache-miss input, cache hit $0.19 
| DeepSeek-V4-Flash-0731 | Demoted (v1) | Unverified | —            | 79.0%              | 83.1% (2.1)   | 1M      | No     | Yes             | July 31 release. Cheapest in table; replaced by Kimi K2.7-Code for Ask this round

### Roster — Alt 2 models

| Model                 | Role        | TS build | SWE-bench Pro | SWE-bench Verified | Terminal-Bench | Context | Vision | Open weights    | Key note                                               |
| --------------------- | ----------- | -------- | ------------- | ------------------ | -------------- | ------- | ------ | --------------- | ------------------------------------------------------ |
| DeepSeek V4 Pro       | Alt 2       | Failed   | 55.4%         | 80.6%              | 44.0%          | 1M      | No     | Yes             | TS build failed in Kilo's own test. Reasoning-only agents 
| Hy3 (Hunyuan 3)       | Alt 2       | Pass     | 59.8%         | 78.2%              | 65.4%          | 256K    | No     | Yes             | ~$0.17     | Free*       | *Free in Kilo Code currently. 99.99% production uptime |
| MiniMax M3 `VERIFIED` | Main        | Pass†    | 59.0%‡        | 80.5%              | 66.0%‡         | 1M      | Yes    | Yes             | †Kilo's own audit: found 13/17 planted TS bugs for $0.07 at 18× less cost. Now in Table 1 for Review/Frontend
| Step 3.7 Flash        | Demoted (v1) | Untested | 56.3%         | 76.5%‡            | 59.5%          | 256K    | Yes    | Yes (Apache 2.0) | Replaced by MiniMax M3 — weaker, less recent verification 

### OpenAI — Frontier

| Model         | Role    | TS build | SWE-bench Pro | SWE-bench Verified | Terminal-Bench | Context | Vision | Open weights | Key note                                                  |
| ------------- | ------- | -------- | ------------- | ------------------ | -------------- | ------- | ------ | ------------ | --------------------------------------------------------- |
| GPT-5.6 Luna `NEW` | Not a fit | Untested | — | — | — | — | — | — | Benchmark, context, capability, and pricing data pending verification |
| GPT-5.6 Terra `NEW` | Not a fit | Untested | — | — | — | — | — | — | Benchmark, context, capability, and pricing data pending verification |
| GPT-5.6 Sol `NEW` | Not a fit | Untested | — | — | — | — | — | — | Benchmark, context, capability, and pricing data pending verification |

### xAI — Frontier (Table 5)

| Model | Role | TS build | SWE-bench Pro | SWE-bench Verified | Terminal-Bench | Context | Vision | Open weights | Key note |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Grok 4.5 `NEW` | Main | Untested | 64.7%* | — | 79.3% (2.1) | 500K | Yes | — | Vendor Pro; independent TB 2.1. Below 200K prompt tokens priced lower; higher rate at 200K+ |

### Watchlist — not in roster

| Model             | Role      | TS build | SWE-bench Pro | SWE-bench Verified | Terminal-Bench | Context | Vision | Open weights | Key note                                                   |
| ----------------- | --------- | -------- | ------------- | ------------------ | -------------- | ------- | ------ | ------------ | -------------------------------------------------------- |
| Gemini 2.5 Flash `NEW` | Not a fit | Untested | — | 63.8%* | — | 1M | Yes | — | *Vendor Verified; requested model, corrected from “Agnes 2.5 Flash” 
| Laguna S 2.1 `NEW` | Not a fit | Untested | 59.4%* | — | 70.2%* | 1M | No | Yes (OpenMDW) | Vendor scores; suite provenance retained 
| Macaron V1 Venti `NEW` | Not a fit | Untested | —‡ | 85.6%‡ | 87.6%‡ | 1M | No | Yes (MIT) | Vendor-only; third-party gateway rate 
| Nemotron 3 Super  | Not a fit | Untested | —             | 60.5%              | —              | 128K    | No     | Yes (NVIDIA) | Self-host  | Self-host   | Best US open-weight comparison model |

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
- `†` = pricing qualifier (for example cache-miss or long-prompt tier)
- `‡` = vendor-reported, pending independent reproduction on standard suites

**TS build** statuses: Pass / Builds / Contested / Unverified / Failed / Untested

---

_Merged · AI_MODELS_REPORT.md × ai_model_report.html · R09 · July 2026 · internal_

_Created with GLM-5.2 High_
