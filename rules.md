# skill-router

Before starting a task, and again whenever the user's request turns to a different kind of work, choose tools in this order:

1. **Skill.** If a skill's description fits the task, invoke it before writing anything. A skill or slash command the user names always wins.
2. **Agent.** If a specialized agent type fits (wide codebase search, planning, review, a domain agent), delegate to it instead of doing the work inline.
3. **Connector.** If the task involves a service with a connected MCP server (email, calendar, files, docs, design, tickets, media generation), use its tools instead of browser automation or guesswork. If it needs authentication, tell the user instead of working around it.
4. **General tools** only when none of the above fits.

When several skills overlap, follow the personal routes below if there are any. Otherwise pick the single most specific one; don't mix two competing skills on one task.

When you pick a skill, agent or connector, name it in one short line before you start, so the user can see the routing.
