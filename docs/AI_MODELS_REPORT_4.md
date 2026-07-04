Confirmed directly against Anthropic's platform docs: Sonnet 5 landed on June 30, 2026, and Anthropic's own effort documentation shows it's the first Sonnet-class model to get the **xhigh** level — Sonnet 4.6 tops out at low/medium/high/max, while Sonnet 5 adds xhigh between high and max, giving it the five-level range you're referring to. That's a genuine new lever, not a rename.

**What each level does for Sonnet 5, per Anthropic's own guidance:** low effort suits high-volume or latency-sensitive, non-coding work; medium is the cost-saving step-down that performs comparably to Sonnet 4.6 at its old default high effort; high is the new default; xhigh is reserved for the hardest coding and agentic tasks; and max is uncapped-token, maximum-capability mode.

**The important nuance for cost decisions:** independent-leaning coverage of the launch benchmarks shows Sonnet 5 beats Sonnet 4.6 across the board — 63.2% vs prior-gen SWE-bench Pro scores, and roughly 1–3 points off Opus 4.8 on tool-use tasks at higher effort. But that gap-closing comes at a cost: at xhigh, Sonnet 5 can burn enough extra reasoning tokens that it ends up costing _more_ than Opus 4.8 for equivalent quality. So xhigh isn't a "cheap Opus" hack — the win is concentrated at low and medium effort, where Sonnet 5 is a clean upgrade over 4.6 at the same or lower cost. Also worth flagging: intro pricing of $2/$10 per million runs only through August 31, 2026, after which it reverts to $3/$15 — the same rate as Sonnet 4.6, offset by a heavier tokenizer.

---

## Updated Claude Tier Table — Opus 4.8 vs Sonnet 5, with Effort

| Agent                   | Claude Model | Effort | Why                                                                                                    |
| ----------------------- | ------------ | ------ | ------------------------------------------------------------------------------------------------------ |
| **Plan**                | Opus 4.8     | Xhigh  | Architectural judgment — Anthropic's own guidance for Opus 4.8 starts at xhigh for coding/agentic work |
| **Code**                | Sonnet 5     | Medium | Anthropic states medium now matches what used to require Sonnet 4.6 at high — same quality, lower cost |
| **Ask**                 | Sonnet 5     | Low    | Lightweight Q&A is exactly the "chat, non-coding" case low effort is built for                         |
| **Debug**               | Opus 4.8     | Xhigh  | Root-cause diagnosis is judgment work; gap to Sonnet 5 narrows but doesn't close cheaply               |
| **Review**              | Opus 4.8     | Xhigh  | Catching subtle flaws is where Opus 4.8's accuracy edge still earns its cost                           |
| **Code Simplifier**     | Sonnet 5     | Medium | Refactoring within known constraints — cost-optimal tier                                               |
| **Documentation**       | Sonnet 5     | Low    | Prose generation, non-coding — no benefit from deeper reasoning                                        |
| **Backend Specialist**  | Opus 4.8     | Xhigh  | Schema/auth/licensing trade-offs carry long-term cost if wrong                                         |
| **Frontend Specialist** | Sonnet 5     | Medium | Pattern-based UI implementation                                                                        |
| **DevOps**              | Sonnet 5     | Medium | Structured, bounded tasks; escalate to Xhigh only for complex pipeline redesigns                       |

**No agent actually moves tiers.** The Opus/Sonnet split you already had (judgment vs. execution) still holds — what's new is that Sonnet 5 gives you a second lever _within_ its own tier. Previously "Sonnet 4.6" was one fixed setting; now you can run the execution-heavy agents at medium (cheaper, matches old high-effort quality) or drop Ask/Documentation to low (cheaper still, since they were never reasoning-bound tasks to begin with). Net effect: your Sonnet-tier bill should go down even though the model itself is more capable, as long as you're deliberate about setting effort explicitly rather than leaving everything on the default high.

One honest caveat: these are Anthropic's own launch-day benchmarks from three days ago — solid enough to act on for internal tooling like this, but worth re-checking once independent evals land over the next few weeks.

**Housekeeping for your Kilo Code tables (1 & 2):** the "Sonnet 4.6 fallback" row should now read **"Sonnet 5 fallback"** — the open-model roster underneath it (GLM-5.2 High / Qwen 3.7 Plus / Hy3) doesn't change, only the Claude-side label it's backing up. Let me know if you'd like the full tables reprinted with that rename applied.
