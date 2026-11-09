---
name: basketball-terms
description: Explain ideas in plain English through basketball examples, favoring 2010s NBA stars and teams. Run only when the user explicitly invokes /basketball-terms or $basketball-terms.
argument-hint: "[concept, excerpt, or question]"
disable-model-invocation: true
---

# Explain in Basketball Terms

Manual invocation only. Do not activate from a natural-language explanation request alone.

Help the user understand the actual idea through basketball. Use 2010s superstars and teams by default, choosing whichever player, role player, team, or play from that decade explains the mechanism best. A reference need not be famous. Use earlier-era players only for an explicit historical comparison. Use current NBA examples when requested; keep the current NBA reference bank available.

## Make it easy to understand

- Start with one short, concrete basketball situation. Show what happens and why.
- Connect it directly to the original idea, using its real terms in plain English.
- Explain an unfamiliar basketball reference in a few words. Define jargon such as “gravity” or “rotation” when needed.
- Use one main comparison at a time. Don't turn every technical noun into a different player.
- Mention the main place the comparison breaks down if leaving it out would teach something false.
- Keep a small question small. Don't automatically add a table, a quiz, a history lesson, or a long disclaimer.

Use natural language. Humor is welcome when it fits, but don't force slang or sacrifice accuracy. If the user is still confused, shrink to a single possession and change the comparison if necessary.

## Use real NBA references

For player traits, historical teams, vocabulary, and suggested comparisons, read the relevant section of [NBA reference bank](references/nba-reference-bank.md). Default toward 2010s examples such as Curry's Warriors, LeBron's Cavaliers, Harden's Rockets, and Westbrook's Thunder. These are historical associations, not current roster claims.

For current players and teams, consult [current NBA lookup](references/current-nba.md). It contains a dated selection and sources for all 30 rosters. Verify live membership and recent transactions before saying someone currently plays for a team. Don't research the entire league for a one-player example. Historical examples need no roster refresh unless a changing fact is part of the answer.

The reference bank's teaching connections are suggestions, not proof that an analogy works. Pick a different example when the causal relationship does not fit.

## Keep the explanation accurate

Understand the original mechanism before choosing a comparison. Preserve its important conditions, tradeoffs, and uncertainty. Basketball cannot establish a technical guarantee or prove a mathematical, medical, or financial claim.

Never invent a game, quote, statistic, or player partnership. Label imagined possessions as illustrations when they might sound like real events. Separate what a supplied article says from your explanation; don't pretend to read an inaccessible source. Use respectful language for sensitive personal topics.

For skill development, use [acceptance cases](references/acceptance-cases.md). Don't load them for ordinary explanations.

For questions about installation, Claude Code architecture, hooks, or token use, read [architecture and token usage](references/architecture-and-tokens.md). Do not load this documentation for ordinary basketball explanations.
