# skill-router

A Claude Code plugin for people with lots of skills, plugins and connectors installed.

Claude can see everything you have installed, but it doesn't always use it. It starts a UI without your design skill, writes an email by hand when the Gmail connector is right there, or keeps going with the tools from the last task after the conversation has moved on. Overlapping plugins make it worse: with three design skills installed, which one should win?

skill-router fixes that with two hooks:

- **At the start of every chat** (and after `/clear` or context compaction) it gives Claude a short set of routing rules: skill first, then a specialized agent, then a connector, then general tools. Your personal routes are added if you have them.
- **On every message** it adds one line asking Claude to re-check the routing when the conversation turns to a different kind of task.

There is no AI call in the hooks. They print text from files, so they're fast and work offline.

## Install

In Claude Code:

```
/plugin marketplace add Hnozaa/skill-router
/plugin install skill-router@skill-router
```

Or from a terminal:

```bash
claude plugin marketplace add Hnozaa/skill-router
claude plugin install skill-router@skill-router
```

Start a new chat afterwards. Hooks load when a session starts.

## Personal routes (recommended)

The general rules work on their own, but routing gets much better when you say which tool wins for which job. Copy [`router.example.md`](router.example.md) to `~/.claude/router.md` and edit it:

```
- Building or redesigning a web UI -> frontend-design (not other design skills unless I name them)
- Reviewing a diff or PR -> /code-review
- Email and calendar -> the Gmail and Google Calendar connectors
```

Use one line per kind of task, and list only things you actually have installed. If you set `CLAUDE_CONFIG_DIR`, the file goes in that directory instead.

## Cost

The rules and your routes are added once per session, about 300 tokens plus your routes file. The per-message reminder is about 35 tokens. Keep `router.md` short, because it's loaded in every chat.

## Requirements

Bash. It's already there on macOS and Linux, and Claude Code on Windows requires Git for Windows, which includes it.

## Uninstall

```bash
claude plugin uninstall skill-router@skill-router
```

## License

MIT
