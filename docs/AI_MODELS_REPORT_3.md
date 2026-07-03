| Agent / Fallback | GLM-5.2 mode | Why |
|---|---|---|
| **Plan** | Max | Architectural decisions — named directly as a Max use case |
| **Code** | High | Everyday generation against a clear spec |
| **Ask** | High | Direct Q&A, no benefit from extra deliberation |
| **Debug** | Max | "Intricate debugging" — named directly as a Max use case |
| **Review** | Max | Catching subtle bugs is exactly where deeper reasoning pays off |
| **Code Simplifier** | N/A — runs on Kimi K2.6 | Not a GLM-5.2 agent in your current roster |
| **Documentation** | High | Prose generation is a "fairly direct" task |
| **Backend Specialist** | Max | Schema/auth/licensing trade-offs — architectural judgment |
| **Frontend Specialist** | High | Pattern-based UI implementation |
| **DevOps** | High | Bounded, structured tasks (escalate to Max only for complex pipeline redesign) |
| **Opus 4.8 fallback** | Max | This fallback exists for your highest-stakes moments — use the deeper mode |
| **Sonnet 4.6 fallback** | High | Sonnet-tier work is volume/speed-oriented by design |

I'm keeping **Kimi K2.6 as Main only for Code Simplifier** — refactoring is closer to disciplined execution within existing constraints than open-ended judgment, and it's the one place Kimi's demonstrated 4,000+ tool-call session endurance and vision input still carry real weight.

One thing worth flagging while we're here: the same research that justified Max mode for Plan and Debug also named **"complex refactors"** explicitly as Max-mode territory — which is literally what Code Simplifier does. If you ever wanted to route Code Simplifier through GLM-5.2 instead of Kimi K2.6, **Max** would be the right setting for it. I kept Kimi K2.6 as Main there last round because of its proven long-session tool-call endurance and vision input, but it's a closer call than the rest of the table — worth testing both on a real refactor task in your monorepo if you want to settle it empirically rather than on benchmarks alone.
