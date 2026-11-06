# Visual design guide

## Structure
- Title (≤ 6 words) and one sentence saying what the visual explains, at the top.
- One reading direction: left→right for request flows, top→bottom for layers/lifecycles.
- Align nodes on a grid (multiples of 20px). At least 40px gap between nodes.
- Group related components in a light, labeled container (e.g. "Data tier").
- At most about 7–9 nodes per diagram or per step. More than that, split into layers (overview first, then zoom in) or steps.
- Numbered step badges (①②③) on the main-path arrows for flows.

## Typography
- One font stack: `system-ui, -apple-system, "Segoe UI", sans-serif`; monospace only for literal requests/keys.
- Sizes: title 20, subtitle 13, node label 14 (semibold), sub-label 12, arrow label 12. Nothing below 11.
- Node text ≤ 3 short words + optional 1-line sub-label. Put longer explanation in the walkthrough.

## Color (stable meanings — always paired with a label, shape, or line style)
| Meaning | Light | Dark | Non-color cue |
|---|---|---|---|
| Neutral component | #f4f5f7 fill / #5b6270 stroke | #23262d / #9aa1ad | solid outline |
| Main/success path | #2f6fdb | #6ea0ff | solid arrow + number |
| Failure / miss path | #c2410c | #fb923c | **dashed** arrow + "miss"/"fail" label |
| Optional / simplified | — | — | dashed outline + "(optional)" |
| Active step (interactive) | #2f6fdb ring | #6ea0ff ring | thicker 3px stroke + "now" tag |

Define colors as CSS variables and switch them under `@media (prefers-color-scheme: dark)`.

## Connectors
- Every important arrow has a short label (verb or payload: "read key", "miss", "write back").
- Arrowheads via `<marker>`. Route orthogonally or straight; avoid crossings — reorder nodes before adding bends.
- Request and response on separate, offset lines rather than a double-headed arrow when direction matters.

## Accessibility & scaling
- Root `<svg viewBox="…" width="100%" role="img" aria-labelledby="t d">` with `<title id="t">` and `<desc id="d">`.
- No fixed pixel width on the root; height follows the viewBox.
- Wide (left→right) SVGs become unreadable below ~500px. For phone-width panels, use a top→bottom layout (see how `stepper.html` switches below 600px).
- Contrast ≥ 4.5:1 for text against its fill in both themes.

## Reusable layouts
- **Request flow** (`templates/request-flow.svg`): client → service → cache/DB with hit and miss paths. Adapt for CDN, rate limiter, read replicas.
- **Step-through** (`templates/stepper.html`): data-driven steps with a Normal/Failure switch. Adapt for queues, retries, leader election, 2PC, saga.
- **Comparison**: two columns of the same skeleton (e.g. write-through vs write-back) with differing arrows highlighted; reuse request-flow shapes.
