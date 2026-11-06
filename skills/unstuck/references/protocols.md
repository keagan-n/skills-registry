# Unstuck protocols

Synthesised from Pólya's *How to Solve It*, CS-education studies of novice problem-solving and debugging, and practitioner frameworks. None has been tested as a complete package. Ask for the next missing step; don't recite the list.

## Any problem

1. **Restate** — inputs, outputs, the rule connecting them, what "done" looks like.
2. **Make it concrete** — 2–3 tiny examples, including an edge case. Draw them.
3. **Find a relative** — a seen problem with the same shape; else a simpler version (sorted input, k = 1, no duplicates).
4. **Get something crude working** — brute force, naive single-server design, or a reliable bug reproduction.
5. **Check by hand** — run the plan on the examples. Every constraint used?
6. **Split known from unknown** — turn each unknown into one specific question.
7. **Write the insight** — one sentence: the key idea and its pattern.

Rough time guide (practitioner rule of thumb): a real attempt of ~20–30 min (easy), 30–45 (medium), 45–60 (hard) before the full solution; climb a hint rung after ~10 min with no new idea.

## DSA / LeetCode

1. Solve 2–3 examples **by hand** — the hand method is often the algorithm.
2. Draw the input: array with indices, tree, graph, grid.
3. Write the brute force and its time/space cost. (If no optimal idea after ~8–10 min, write it.)
4. Read the constraints — what does each rule out?
5. What work does the brute force repeat?
6. Trace the candidate by hand **before** coding.
7. Code it; then "what input breaks this?"

Cue → technique (community heuristics, not research):

| Cue | Try |
|---|---|
| repeated lookup | hash map |
| repeated subproblem | dynamic programming |
| repeated min / max | heap or monotonic stack |
| sorted input | binary search or two pointers |
| contiguous range + optimise | sliding window |
| n ≤ ~20 | exponential OK |
| n ≤ ~10³ | O(n²) OK |
| n ≤ ~10⁵ | O(n log n) or better |

## System design

No research exists on how system design is best learned; this is a practitioner framework.

1. **What it does** — 3–5 verbs ("post, follow, view feed").
2. **How well** — scale, latency, consistency, availability.
3. **Rough numbers** — requests/sec, storage, read/write ratio.
4. API and data model.
5. Naive single-server design that works for 10 users.
6. "What breaks first at my scale?" — deep-dive 2–3 areas.
7. Trade-offs, and what changes at 10×.

Do not invent company-specific interview expectations.

## Debugging (scientific debugging)

1. Reproduce reliably; write the exact input/command.
2. Observed vs expected — one line each.
3. **One** hypothesis; predict what a test will show if it's true.
4. Test it: print, breakpoint, assertion.
5. Keep a running list (in the conversation) of hypotheses tried and results — never retry one.
6. Bisect: half the input, half the code, or `git bisect`.
7. Shrink to the smallest failing input.
8. Explain the suspect code aloud, line by line.
9. Usual suspects: off-by-one, loop bounds, integer arithmetic.

Anti-pattern: tinkering — random edits and reruns. Finding the bug is the hard part, not fixing it.

## Concept

Diagnose the source first:
- **Missing term/concept** → define it briefly.
- **Missing prerequisite** → name it, cover just enough.
- **Too much at once** → write it down, draw it, or shrink to 3 nodes / 3 elements and trace.

Before explaining, optionally ask the user to commit to answers on 2–3 specific questions ("what happens to keys when a node joins?"). If an explanation doesn't land, switch angle on the *same* idea.

## Self-questions when the mind goes blank

- What exactly are the input, the output and the rule connecting them?
- Can I solve a tiny example by hand right now?
- What's the dumbest correct solution?
- Have I seen a problem with the same unknown?
- Can I solve a simpler version first?
- Which constraint haven't I used?
- What work am I repeating?
- Did I check my plan on an example before coding?
- It "works" — what input breaks it?
