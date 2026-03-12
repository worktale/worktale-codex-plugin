# Worktale Skill for Codex CLI

**AI session narration for your daily work journal.**

Git captures the *what*. This plugin captures the *why*.

When you activate the Worktale skill in [Codex CLI](https://github.com/openai/codex), your AI coding agent automatically narrates each commit — adding intent, decisions, and context to your [Worktale](https://worktale.org) daily narrative.

## Install

Copy the skill to your Codex skills directory:

```bash
# Clone and install
git clone https://github.com/worktale/worktale-codex-plugin.git
cp -r worktale-codex-plugin/skills/worktale ~/.codex/skills/worktale
```

Or manually create `~/.codex/skills/worktale/SKILL.md` with the contents from this repo.

Requires the [Worktale CLI](https://www.npmjs.com/package/worktale) **v1.1.0+**:

```bash
npm install -g worktale@latest
cd your-repo
worktale init
```

## Usage

Start Codex with skills enabled:

```bash
codex --enable skills
```

The agent will automatically detect and activate the Worktale skill when relevant. After every commit it makes, it runs:

```bash
worktale note "Refactored auth middleware for compliance — replaced session token storage"
```

Notes accumulate throughout the day. View them with:

```bash
worktale digest    # End-of-day summary with your notes
worktale dash      # Interactive TUI dashboard
```

## What gets captured

The agent writes 1-2 sentence notes focused on:

- **Intent** — why the change was made
- **Decisions** — trade-offs and alternatives considered
- **Problems solved** — bugs found, root causes identified

It does *not* duplicate what git already tracks (file paths, line counts, diffs).

## How it works

1. Codex loads the skill from `~/.codex/skills/worktale/SKILL.md`
2. The skill prompt instructs the agent to run `worktale note "..."` after each commit
3. `worktale note` appends to the `user_notes` field in your local Worktale database
4. Notes appear in `worktale digest`, the TUI dashboard, and (eventually) your Worktale Cloud portfolio

All data stays local. Nothing leaves your machine.

## Links

- [Worktale CLI](https://github.com/worktale/worktale-cli)
- [Worktale website](https://worktale.org)
- [Documentation](https://worktale.org/docs.html)
- [Claude Code Plugin](https://github.com/worktale/worktale-plugin)

## License

MIT
