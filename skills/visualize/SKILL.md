---
name: visualize
description: Visual Explainer. Produces polished teaching visuals — static SVG diagrams or small interactive step-through pages — for system-design and technical concepts. Use this whenever the user wants to see how something works, such as "draw this", "show me how this works", "make a diagram", "visualize this request flow", "map out the architecture", "step me through what happens when…", or "explain this with a diagram" — even if they never say "visualize". Do NOT use for concepts a short paragraph handles better, and do not quiz the user (use recall).
argument-hint: "[concept or flow]"
---

# Visual Explainer

Make one clear teaching visual that shows the real mechanism, plus a short plain-language walkthrough. Read `references/design-guide.md` before drawing. Start from a template in `templates/` when one fits.

## Choose the format

| Concept | Format |
|---|---|
| Architecture, relationships, comparisons, reference views | **Static SVG** (`templates/request-flow.svg`) |
| Events over time, revealing steps, or switching normal vs failure | **Interactive page** (`templates/stepper.html`) |
| A single idea a paragraph explains well | **No visual** — just explain it |

## Render with what this surface supports

Use the first one available:
1. An inline visual/widget tool (e.g. a `show_widget`-style tool) — SVG or HTML inline in chat.
2. An Artifact tool — publish the HTML page.
3. Otherwise write a `.svg` or `.html` file and give the user its path, and say you could not preview it.

## Teaching rules

- Show the main path first; exceptions and secondary details after.
- Trace **one concrete** request, message, or state change (e.g. `GET /user/42`).
- Keep each diagram, or each step of a step-through, to about **7–9 nodes**. If it needs more, split it into layers or steps.
- Explain the important arrows and design decisions in plain language.
- Visibly mark assumptions, simplifications, and optional components (dashed outline + "(optional)" / "simplified" label).
- Never imply guarantees the components don't provide. Example: a queue with acks gives **at-least-once** delivery; a consumer crash after processing but before ack causes a **duplicate**, so consumers must be idempotent. Do not draw "exactly once" unless the design actually achieves it and you say how.
- For code visuals, depicted state must match the actual code — read it first.
- End with a short walkthrough (3–6 numbered sentences matching the numbered steps). An understanding question is optional in explain mode.

## Interactive rules

- Only useful controls: Previous, Next, Reset, and a Normal/Failure switch when a failure path matters.
- Show the current step clearly ("Step 3 of 6") and highlight the active element.
- Include a **Predict** toggle, off by default. When on, Next first asks "what happens next?" (with a step-specific question where useful) and reveals the step on the second press. `templates/stepper.html` implements this.
- Keyboard: ←/→ for steps, R for reset. Buttons are real `<button>`s.
- Layout must work at narrow panel widths (SVG scales via `viewBox`).
- Every control must actually work. Never present a static SVG as interactive.

## Quality gate (before delivering)

1. **Check every arrow against the source.** For each arrow, confirm its direction, its order, and that the source (article, code, or established protocol behaviour) actually supports it. A plausible-looking wrong arrow, like a misordered handshake, is the most harmful error and no renderer will catch it. If the source doesn't settle an arrow, label it as an assumption.
2. Render or preview it if the surface allows (inline widget, artifact, or browser pane).
3. Inspect for: clipped text, overlapping nodes or labels, crowded labels, ambiguous or unlabeled arrows, low contrast, dark-mode legibility, and layout breakage at narrow width.
4. For interactive pages, click through every control in both scenarios, with Predict on and off.
5. Fix what you find. If you could not visually inspect it, say so — do not claim it was verified.

## Boundaries

No decorative dashboards, unnecessary controls, or excessive animation. No mandatory redraws or exports. Do not edit V6 or other recruiting records.
