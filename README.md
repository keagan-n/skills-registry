# skills-registry

Five personal learning skills, published from GitHub as the **learning** Claude Code plugin in the **keagan-skills** marketplace.

## Install in Claude Code

Run these inside Claude Code (not your shell):

```text
/plugin marketplace add keagan-n/skills-registry
/plugin install learning@keagan-skills
```

Choose user scope to make the plugin available across projects. This private repository requires GitHub access. Claude downloads a managed plugin copy; no Documents checkout or hand-created symlinks are required.

On newer Claude Code versions supporting the combined marketplace flag, the equivalent is:

```text
/plugin install learning --marketplace keagan-n/skills-registry
```

The two-command form works with the installed version checked during packaging (2.1.158). Follow Claude's reload prompt or start a new session after installation.

## Commands

| Command | Purpose | Automatic selection |
|---|---|---|
| `/learning:help-me-learn` | Explain technical study material | Allowed |
| `/learning:visualize` | Draw diagrams and interactive explanations | Allowed |
| `/learning:recall` | Check understanding, one question at a time | Allowed |
| `/learning:unstuck` | Guide practice with graduated hints | Disabled: manual only |
| `/learning:basketball-terms` | Explain simply through basketball, favoring 2010s examples | Disabled: manual only |

Example:

```text
/learning:basketball-terms explain database indexes
```

Existing standalone installations keep their plain commands, such as `/basketball-terms`. Installing the plugin alongside those copies creates two sources of the same skills. After verifying the plugin, remove only the old symlinks from `~/.claude/skills/` to avoid duplicate loading. Keep standalone Codex installations separate; the Claude plugin installation does not configure Codex.

## Updates

Use `/plugin` to manage marketplace updates and auto-update settings. From a shell with Claude Code installed:

```bash
claude plugin marketplace update keagan-skills
claude plugin update learning@keagan-skills
```

Reload as instructed or start a new session. Plugin updates come from GitHub. Local development changes are not published until committed and pushed. Bump the version in both manifests when releasing plugin changes.

## What is packaged

The root `.claude-plugin/plugin.json` names the plugin. `.claude-plugin/marketplace.json` lists it with the repository root as its source. Claude discovers the five folders under `skills/` automatically. References and visualization templates stay alongside their skills. No hooks, MCP servers, or agents are added by this package.

- [Basketball architecture, LLM, hooks, and token usage](skills/basketball-terms/references/architecture-and-tokens.md)
- [NBA reference bank](skills/basketball-terms/references/nba-reference-bank.md)
- [Dated current NBA lookup](skills/basketball-terms/references/current-nba.md)
- [Acceptance cases](EVALS.md)

The basketball skill retains its Codex metadata with automatic invocation disabled. Its current roster bank is dated and requires live verification for current claims.

## Standalone installation alternative

For plain slash commands, use a GitHub-backed checkout under `~/.local/share/skills-registry` and link the desired skill folders into `~/.claude/skills/`. This is the earlier standalone setup, not a prerequisite for the plugin. Its manual update command is:

```bash
git -C ~/.local/share/skills-registry pull --ff-only
```

## Validation

Validate manifests with `claude plugin validate .` and `claude plugin validate .claude-plugin/plugin.json`. The existing acceptance cases describe behavioral checks; they are not evidence of completed live evaluations. Confirm the namespaced commands in a fresh installed session.
