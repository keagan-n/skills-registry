# skills-registry

My Claude skills, versioned in one place.

## Learning skills

Four Claude skills: **help-me-learn** (Reading Companion), **visualize** (Visual Explainer) and **recall** (Recall and Transfer Coach) from the November 6, 2026 spec, plus **unstuck** (Unstuck Coach), added the same day from the "Stop staring" cheat sheet.

**Status: installed for Claude Code on Nov 6, 2026** at `~/.claude/skills/{help-me-learn,visualize,recall,unstuck}`. Not yet confirmed in a new session's `/` menu. Not uploaded to claude.ai.

```
skills-registry/
├── skills/
│   ├── help-me-learn/SKILL.md
│   ├── visualize/
│   │   ├── SKILL.md
│   │   ├── references/design-guide.md
│   │   └── templates/request-flow.svg   (cache hit/miss, static)
│   │   └── templates/stepper.html       (queue ack, interactive)
│   ├── recall/SKILL.md
│   └── unstuck/
│       ├── SKILL.md
│       └── references/protocols.md      (DSA, system design, debugging, concept)
├── project-instructions.md   (shared style + V6 boundaries)
├── EVALS.md                  (acceptance cases A–S)
└── README.md                 (this file: install + quick reference)
```

## Install

### Claude Code (CLI or desktop Code tab)
User-level skills live in `~/.claude/skills/<name>/SKILL.md`. Each skill folder's name becomes its slash command.

```bash
git clone https://github.com/keagan-n/skills-registry.git
```

```bash
mkdir -p ~/.claude/skills && cp -R skills-registry/skills/help-me-learn skills-registry/skills/visualize skills-registry/skills/recall skills-registry/skills/unstuck ~/.claude/skills/
```

Start a new session afterwards. Verify by typing `/` and checking that `help-me-learn`, `visualize`, `recall` and `unstuck` appear in the list.

Optional: append the block from `project-instructions.md` to `~/.claude/CLAUDE.md`.

### claude.ai (web / desktop chat)
Zip each skill folder separately (the zip must contain the folder with `SKILL.md` inside) and upload it under **Settings → Capabilities → Skills**. Paste `project-instructions.md` into your study Project's instructions.

```bash
cd skills-registry/skills && for s in help-me-learn visualize recall unstuck; do zip -r "../$s.zip" "$s"; done
```

On claude.ai, skills are selected automatically from your natural request (or from the skill picker); bare slash commands like `/help-me-learn` are **not** guaranteed there. Confirm after uploading.

## Quick reference

| Skill | Claude Code command | Natural requests (any surface) |
|---|---|---|
| Reading Companion | `/help-me-learn [excerpt or topic]` | "Explain this section", "Help me understand this", "Walk me through this Hello Interview article", "What does this mean?" |
| Visual Explainer | `/visualize [concept]` | "Draw this for me", "Show me how this works", "Make a diagram", "Visualize this request flow" |
| Recall Coach | `/recall [topic]` | "Quiz me on this", "Check my understanding", "See what I remember", "Give me a different scenario" |
| Unstuck Coach | `/unstuck [problem]` | **Command only in Claude Code** — natural requests won't trigger it, so "I'm stuck on this bug" in a coding project still gets a normal fix. |

Combined: "Explain this with a diagram" → help-me-learn handles it and produces the visual itself; no need to call both.

**unstuck on claude.ai:** `disable-model-invocation` is a Claude Code setting. claude.ai may ignore it and pick the skill from your request; its description asks to run only on `/unstuck`, but that isn't guaranteed there.

Inside unstuck, say "hint" to climb one rung (category → step away → key insight → full solution → similar problem), or "just tell me" to get the answer.

Switch mode in plain words: "just tell me the answer", "quiz me instead", "keep it to 10 minutes".

Note: the Claude Code commands above become real only after install. A plugin-packaged version would be namespaced (e.g. `/learning:help-me-learn`); this package uses plain user skills, so the commands are un-namespaced.
