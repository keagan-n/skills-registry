# Evaluation cases

Run each prompt in a fresh session after installing. Record what happened, not how polished it looked. Results marked **not yet run** have not been tested with the installed skills.

| # | Prompt | Pass looks like | Result |
|---|---|---|---|
| A | `/help-me-learn` + paste an unfamiliar Hello Interview section (e.g. consistent hashing) | Central idea → mechanism → one example → tradeoff. No attempt demanded first. ≤ 1 optional question. | not yet run |
| B | "In this paragraph, what does 'fan-out on write' mean?" | 2–5 sentences answering only that. No lesson, no quiz. | not yet run |
| C | `/visualize cache hit vs miss for GET /user/42` | Clean SVG; hit and miss paths both labeled; miss path distinguishable without color; render checked. | Template `request-flow.svg` rendered and inspected (see below). Live skill: not yet run |
| D | "Explain what happens if a consumer crashes before acking" | Says at-least-once; names duplicate delivery; recommends idempotency; never claims automatic exactly-once. | Template `stepper.html` covers this; clicked through both scenarios (see below). Live skill: not yet run |
| E | `/recall load balancing` | One question at a time; no answer leaked in the question; specific feedback naming the exact gap. | not yet run |
| F | During recall, answer with a correct but non-textbook explanation | Accepted as correct; feedback on reasoning, not wording. | not yet run |
| G | Same request three ways: `/help-me-learn X`, "help me understand X", "explain X" | Same workflow and shape each time. | not yet run |
| H | "I have 10 minutes — quiz me on caching" | One core question, one follow-up at most, stops cleanly, no homework. | not yet run |
| I | `/help-me-learn` + a paywalled Hello Interview URL | Says it can't read it; asks for the excerpt; does not summarize from guesses. | not yet run |
| J | "Mark me as mastered on caching" during recall | Declines to assign a mastery or readiness rating and writes nothing anywhere; offers an observed-only summary instead. | not yet run |
| K | "I still don't get how consistent hashing rebalances" after an explanation | Diagnoses the source (term / prerequisite / overload), shrinks to a tiny example, tries a different angle — not a louder repeat. | not yet run |
| L | During recall, give a confidently wrong answer | Corrects it specifically, then retests with a changed example before the session ends. | not yet run |
| M | During recall, say "hint" three times | Category → key insight → worked explanation, one rung per request; never jumps to the answer on the first "hint". | not yet run |
| O | `/unstuck` + a medium LeetCode problem with "I've been staring for 30 min" | Asks what's written so far; asks for hand-solved examples or brute force; no code or solution given. | not yet run |
| P | In unstuck, say "hint" four times | Category → step-away offer → key insight → full labelled solution; one rung per message. | not yet run |
| Q | In unstuck, say "just tell me the answer" on the first message | Gives the answer, then offers (doesn't force) the why-walkthrough. | not yet run |
| R | In a coding project, "I'm stuck on this bug" without `/unstuck` | unstuck does **not** load; normal debugging help. | not yet run |
| S | `/unstuck` on a real work bug where the user says they need it fixed now | Gives the fix directly and says why it isn't coaching. | not yet run |
| N | `/visualize` a TCP handshake | Arrow order matches the protocol; any unsupported arrow labelled as an assumption; ≤ 9 nodes. | not yet run |

Compare against an ordinary Claude reply (skills disabled) for clarity, misconception correction, and later unaided application. Visual polish, note volume, and same-session fluency alone don't count as evidence of better learning.

## Template inspection notes (Nov 6, 2026)
Checked in the Claude desktop browser pane, dark color scheme only.
- `request-flow.svg` (case C): all seven steps labeled, miss path dashed + orange + "miss" text, no overlaps after one fix (the ① label was touching the App server box; node shifted right). At phone width (375px) the static SVG scales down until its text is too small to read. Use it in a chat panel or desktop view, or redraw it vertically for phones.
- `stepper.html` (case D): Next/Previous/Reset, both scenario buttons, and ←/→/R keys all work; Next disables on the last step. Failure path shows crash → timeout redelivery → idempotency check → ack, and states at-least-once. The first version had unreadable text at 375px, so I added a vertical layout below 600px and re-checked it. No console errors.
- `stepper.html` Predict mode (added later the same day): with Predict on, Next shows the question while the diagram stays on the previous state, then "Reveal →" shows the step. Previous while asking backs out cleanly; turning Predict off mid-question reveals; P key toggles. Step-specific questions appear on steps 4–6 of the crash scenario.
- Not checked: light mode rendering, screen-reader output.
