# Learning skills

Five skills for Claude Code, installed together from this GitHub repository.

## Install

Run these **inside Claude Code**:

```text
/plugin marketplace add keagan-n/skills-registry
/plugin install learning@keagan-skills
```

Choose **user scope** to use the skills across projects. This private repo requires GitHub access. Follow Claude's reload prompt or start a new session, then type `/learning:` to find the commands. No manual cloning or symlinks needed.

## Use

| Command | What it does | Trigger |
|---|---|---|
| `/learning:help-me-learn` | Explain technical material clearly | Manual or automatic |
| `/learning:visualize` | Draw diagrams and interactive explanations | Manual or automatic |
| `/learning:recall` | Check understanding, one question at a time | Manual or automatic |
| `/learning:unstuck` | Work through practice problems with hints | Manual only |
| `/learning:basketball-terms` | Explain through basketball, favoring 2010s NBA examples | Manual only |

Add your topic after the command:

```text
/learning:basketball-terms explain database indexes
```

If you previously installed standalone copies, verify the plugin works before removing the old skill symlinks from `~/.claude/skills/`. The Claude plugin does not install skills in Codex.

## Update

Use `/plugin` to manage updates or enable automatic updates. From your terminal:

```bash
claude plugin marketplace update keagan-skills
claude plugin update learning@keagan-skills
```

Follow the reload instructions or start a new session.

## Details

- [Architecture, hooks, and token usage](skills/basketball-terms/references/architecture-and-tokens.md)
- [NBA examples](skills/basketball-terms/references/nba-reference-bank.md) and [dated roster lookup](skills/basketball-terms/references/current-nba.md)
- [Evaluation cases](EVALS.md)
