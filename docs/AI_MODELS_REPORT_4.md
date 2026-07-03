## New Table — Claude Tier per Agent (Opus 4.8 vs Sonnet 4.6)

| Agent                   | Claude Model | Why                                                                                                   |
| ----------------------- | ------------ | ----------------------------------------------------------------------------------------------------- |
| **Plan**                | Opus 4.8     | Architecture decisions are exactly where the Kilo test showed models diverge most — worth the premium |
| **Code**                | Sonnet 4.6   | Routine generation against a clear spec; Sonnet's 1M context and lower cost fit                       |
| **Ask**                 | Sonnet 4.6   | Lightweight Q&A, no frontier reasoning needed                                                         |
| **Debug**               | Opus 4.8     | Diagnosing root cause is a judgment task, same family as Plan                                         |
| **Review**              | Opus 4.8     | 4× lower code flaw miss rate vs 4.7 matters most where review quality is the entire point             |
| **Code Simplifier**     | Sonnet 4.6   | Refactoring within existing constraints, not open-ended judgment                                      |
| **Documentation**       | Sonnet 4.6   | Prose generation, well within Sonnet's range, cost-conscious                                          |
| **Backend Specialist**  | Opus 4.8     | Schema/auth/licensing trade-offs are judgment calls with long-term cost if wrong                      |
| **Frontend Specialist** | Sonnet 4.6   | Pattern-based UI implementation, mechanical relative to backend decisions                             |
| **DevOps**              | Sonnet 4.6   | Structured, bounded tasks (Dockerfiles, CI YAML)                                                      |

Opus 4.8 takes the judgment-heavy agents (Plan, Debug, Review, Backend Specialist), Sonnet 4.6 takes the execution-heavy ones. That consistency is a good sign the underlying logic holds, independent of which vendor's model you're routing through.
