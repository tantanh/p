I'm moving GLM-5.2 into Main for **Plan, Debug, Backend Specialist, DevOps, and Opus 4.8 fallback** — these all reward "deciding what to build" over "following a spec." I'm keeping **Kimi K2.6 as Main only for Code Simplifier** — refactoring is closer to disciplined execution within existing constraints than open-ended judgment, and it's the one place Kimi's demonstrated 4,000+ tool-call session endurance and vision input still carry real weight.

---

## Table 1 — Expanded Roster (3 models per column)

| Agent / Fallback        | Main         | Alt 1            | Alt 2           |
| ----------------------- | ------------ | ---------------- | --------------- |
| **Plan**                | GLM-5.2 ⬆    | MiMo V2.5-Pro    | DeepSeek V4 Pro |
| **Code**                | GLM-5.2      | Qwen 3.7 Plus    | Hy3             |
| **Ask**                 | GLM-5.2      | Kimi K2.7-Code⏳ | DeepSeek V4 Pro |
| **Debug**               | GLM-5.2 ⬆    | MiMo V2.5-Pro    | DeepSeek V4 Pro |
| **Review**              | MiniMax M3 ⬆ | MiMo V2.5-Pro    | Qwen 3.7 Max    |
| **Code Simplifier**     | Kimi K2.6    | Qwen 3.7 Plus    | Hy3             |
| **Documentation**       | GLM-5.2 ⬆    | Qwen 3.7 Plus    | Hy3             |
| **Backend Specialist**  | GLM-5.2 ⬆    | MiMo V2.5-Pro    | Hy3             |
| **Frontend Specialist** | GLM-5.2      | Qwen 3.7 Plus    | Hy3             |
| **DevOps**              | GLM-5.2 ⬆    | Qwen 3.7 Plus    | Hy3             |
| **Opus 4.8 fallback**   | GLM-5.2 ⬆    | MiMo V2.5-Pro    | DeepSeek V4 Pro |
| **Sonnet 4.6 fallback** | GLM-5.2      | Qwen 3.7 Plus    | Hy3             |

⬆ = switched this round. Review's Main also moved — to **MiniMax M3**, not GLM-5.2 — because the Kilo bug-finding audit is its proven specialty; Qwen 3.7 Max steps down to Alt 2 there, since GLM-5.2 now beats it on SWE-bench Pro too (62.1 vs 60.6) and has independent verification Qwen Max lacks.

**3 per column:** Main = GLM-5.2, Kimi K2.6, MiniMax M3 · Alt 1 = MiMo V2.5-Pro, Qwen 3.7 Plus, Kimi K2.7-Code · Alt 2 = DeepSeek V4 Pro, Hy3, Qwen 3.7 Max

---

## Table 2 — Lean Roster (2 models per column)

| Agent / Fallback        | Main      | Alt 1         | Alt 2           |
| ----------------------- | --------- | ------------- | --------------- |
| **Plan**                | GLM-5.2 ⬆ | MiMo V2.5-Pro | DeepSeek V4 Pro |
| **Code**                | GLM-5.2   | Qwen 3.7 Plus | Hy3             |
| **Ask**                 | GLM-5.2   | Qwen 3.7 Plus | DeepSeek V4 Pro |
| **Debug**               | GLM-5.2 ⬆ | MiMo V2.5-Pro | DeepSeek V4 Pro |
| **Review**              | GLM-5.2   | MiMo V2.5-Pro | Hy3             |
| **Code Simplifier**     | Kimi K2.6 | Qwen 3.7 Plus | Hy3             |
| **Documentation**       | GLM-5.2   | Qwen 3.7 Plus | Hy3             |
| **Backend Specialist**  | GLM-5.2 ⬆ | MiMo V2.5-Pro | Hy3             |
| **Frontend Specialist** | GLM-5.2   | Qwen 3.7 Plus | Hy3             |
| **DevOps**              | GLM-5.2 ⬆ | Qwen 3.7 Plus | Hy3             |
| **Opus 4.8 fallback**   | GLM-5.2 ⬆ | MiMo V2.5-Pro | DeepSeek V4 Pro |
| **Sonnet 4.6 fallback** | GLM-5.2   | Qwen 3.7 Plus | Hy3             |

**2 per column:** Main = GLM-5.2, Kimi K2.6 · Alt 1 = MiMo V2.5-Pro, Qwen 3.7 Plus · Alt 2 = DeepSeek V4 Pro, Hy3

Note: Kimi K2.6 keeps just one Main slot here (Code Simplifier) — it doesn't disappear from the roster, it's just no longer the right tool for judgment-heavy work now that GLM-5.2 has both the benchmark lead and a real demonstrated planning edge.
