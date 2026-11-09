# Behavioral acceptance cases

These are proposed checks, not completed evaluations. Run each in a fresh session with the skill available, and compare against a response without it. Judge causal accuracy and the ability to understand the original idea, not the number of NBA references.

| Request | Pass criteria |
|---|---|
| Explain caching in basketball terms. | A coherent scenario distinguishes fast reuse from retrieving or computing again, translates back to cache terms, and does not suggest every stored answer stays valid forever. |
| Explain replication versus sharding in NBA terms. | Distinguishes copies of the same data from partitioning different data. Does not imply five players on a court are five full replicas. Marks an analogy change if needed. |
| Explain at-least-once delivery in basketball terms. | Models retry after uncertain acknowledgment, including possible duplicates. Does not claim a retry guarantees exactly once. |
| What is opportunity cost? One sentence, basketball terms. | Gives a concise basketball choice and the value of the best forgone alternative. Does not launch a full lesson. |
| Explain compound interest using my favorite team, the Bulls. | Uses a coherent hypothetical if helpful; preserves growth on accumulated interest and avoids a claim about guaranteed investment returns. |
| Explain TCP congestion control; I only know basic basketball. | Uses accessible basketball vocabulary, distinguishes feedback from blind sending, and identifies relevant limits instead of inventing exact protocol equivalents. |
| Use this season's Lakers roster to explain load balancing. | Verifies roster facts when available or labels a hypothetical; explains distribution of work without claiming all tasks or workers are identical. |
| Explain quantum entanglement as two teammates texting each other instantly. | Corrects the instant-messaging premise; does not imply faster-than-light communication. Uses only a limited analogy if appropriate. |
| Explain my grief in NBA terms. | Responds with care, avoids ranking pain or joking about people, and makes only a modest analogy without diagnostic claims. |
| Who won the 1998 NBA Finals? | Answers the sports question directly; does not force a cross-domain analogy. |
| I still don't get why adding servers doesn't always help. | Shrinks to a concrete bottleneck, distinguishes parallelizable work from shared or serial constraints, then translates back. |

An answer passes only when both the basketball account and the original-domain explanation are accurate. A fluent analogy that teaches a false equivalence fails.

## Manual invocation and preferences

- `/basketball-terms explain caching`: activates in Claude Code and explains directly.
- `$basketball-terms explain caching`: activates in Codex.
- `Explain caching in basketball terms` without selecting the skill: must not automatically load this manual-only skill. A normal answer may still honor the user's requested style.
- A general explanation uses 2010s examples; earlier legends appear only in an explicit historical comparison.
- A request for current NBA examples can use the dated current bank, with live verification for current claims.

Installation and policy checks can be verified statically. Fresh-session menu discovery and behavioral cases still require a live run.
