# team-flow

Instructions for AI agents that pass work through a team: **PM → Dev → QA → PM**.

Every person works with their own agent, in their own project folder, on their own computer. Each task moves as one file per role, all starting with the same header, so every role sees the full picture: what the client asked, what changed in the code, and what was checked.

## Start

1. Open an empty project folder in your agent (a desktop app, a CLI — any agent that reads files).
2. Give it the link to this repository and say, in your own language: *"Set up team-flow, I'm the PM"* (or Dev, QA).
3. If a teammate sent you a task file, attach it: the agent takes the project data from its header.

The agent reads [kit/START.md](kit/START.md) and:

- explains in a few lines what it is about to do;
- looks around the folder by itself (site code, existing tasks);
- asks once for missing links, and once which connectors (task tracker, code host, chat) you have — read access only;
- shows what it will create and waits for your yes;
- creates locally: `project.md`, `tasks/`, `media/`, a copy of the kit in `.team-flow/`, and `AGENTS.md` / `CLAUDE.md` / `GEMINI.md` so every new session picks it up.

Nothing is cloned, connected or sent.

## How a task moves

| Role | You say | The agent writes |
| --- | --- | --- |
| PM | "here is what the client sent" (texts, screenshots) | `tasks/CU-001/CU-001-pm.md`: what to do, numbered "Done when" items, where it is in the code |
| Dev | "take CU-001" | `CU-001-dev.md`: what changed, where in the code, against every item |
| QA | "check CU-001" | `CU-001-qa.md`: what was seen on the site and in the code, ✅ / ❌ per item |

You pass the files to the next role yourself, or tell your agent to attach them in a connected task tracker.

`project.md` keeps the project's mini report: one row per task with the current state of every role.

## What the agent does and never does

- Reads by default. Writes only local files in the project folder, and only after your yes.
- Talks to you in your language. Writes files in English.
- Does an action outside your computer (attach, comment, post, push) only when you tell it to do exactly that. Never on its own, never as a suggestion.
- Never asks for passwords, tokens, admin or write access.

Full rules: [kit/RULES.md](kit/RULES.md).

## Inside

```text
kit/
├── START.md       set up, and what to do at the start of every session
├── RULES.md       shared rules: files, header, checks, local vs external, never
├── roles/         pm.md, dev.md, qa.md — steps per role
└── templates/     header.md (shared header), project.md, pm.md, dev.md, qa.md
```
