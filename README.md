# team-flow

Instructions for AI agents that pass work through a team: **PM → Dev → QA → PM**.

Every person works with their own agent, in their own project folder, on their own computer. Each task moves as one file per role, all starting with the same header, so every role sees the full picture: what the client asked, what changed in the code, and what was checked.

> **Before you start**
> - **Early version.** Tested only in a sandbox on a demo site, not on live projects yet. Expect rough edges and tell us what breaks.
> - **Access to this repository.** If it is private, your agent can read the link only with access to it. Otherwise download the `kit/` folder and give your agent its path.
> - **No automatic sync.** Task files move between people by hand or through a connected task tracker (e.g. ClickUp). Nothing syncs on its own: pass your file on when you finish.

## In one minute

team-flow is a set of instructions for an AI agent, so that the PM, the developer and the QA pass tasks in one format.

1. **The PM** gets a request from the client. The agent turns it into a task file: what to do, and how to check it is done.
2. **The developer** gets that file. The agent helps make the changes and writes down what changed and where in the code.
3. **The QA** gets both files. The agent checks the result and writes down what works and what does not.

**Why:** the whole history of a task is in one place. No searching through chats, no asking again.

Give your agent the link to this repository and ask "what is this?" — it explains the same in your language, and sets nothing up until you tell it your role.

## Start

1. Open an empty project folder in your agent (a desktop app, a CLI — any agent that reads files).
2. Give it the link to this repository and say, in your own language: *"Set up team-flow, I'm the PM"* (or Dev, QA).
3. If a teammate sent you a task file, attach it: the agent takes the project data from its header.

The agent reads [kit/START.md](kit/START.md) and:

- explains in a few lines what it is about to do;
- looks around the folder by itself (site code, existing tasks);
- asks once for missing links, and once which connectors (task tracker, code host, chat) you have — read access only;
- shows what it will create and waits for your yes;
- creates locally only `project.md`, a copy of the kit in `.team-flow/`, and `AGENTS.md` (role, nick, where the kit is) with one-line `CLAUDE.md` and `GEMINI.md` that import it, so every new session of any agent picks it up. `tasks/` appears with the first task.

Nothing is cloned, connected or sent.

## Folder layout

One project, one folder. You open every session for that project in its folder.

```text
work/                      your general work folder
├── project-a/             open the agent here
│   ├── AGENTS.md          role, nick, where the kit is
│   ├── CLAUDE.md          @AGENTS.md (one import line)
│   ├── GEMINI.md          @AGENTS.md (one import line)
│   ├── project.md         your mini report of the project
│   ├── .team-flow/        local copy of the kit
│   ├── tasks/CU-001/      the task's files: yours and the ones other roles pass you
│   └── site/              developers only: the site code, its own git
└── project-b/
```

These are defaults. If your project already has its own structure (a tasks folder, notes, code in `src/`), the agent maps it in "Paths" in `AGENTS.md` instead of creating duplicates, and every rule follows that map.

The agent decides where to set up by itself: in the folder you opened, if it is a project folder; in a new `./<project>/` subfolder, if you opened a general work folder; and if you opened the site's code repository, it asks once whether to use the parent folder, so team-flow files stay out of the site's git.

## How a task moves

| Role | You say | The agent writes |
| --- | --- | --- |
| PM | "here is what the client sent" (texts, screenshots) | `tasks/CU-001/CU-001-pm.md`: what to do, numbered "Done when" items, where it is in the code |
| Dev | "take CU-001" | `CU-001-dev.md`: what changed, where in the code, against every item |
| QA | "check CU-001" | `CU-001-qa.md`: what was seen on the site and in the code, ✅ / ❌ per item |

Every person writes only their own file. The first person on a role is the main one (`CU-001-dev.md`); anyone who joins adds their own file with their nick (`CU-001-dev-max.md`). Each file says who filled it and which items it covers. Other specialists (design, content, …) add their file the same way.

You pass the files to the next role yourself, or tell your agent to attach them in a connected task tracker.

`project.md` keeps the project's mini report: one row per task with the current state of every role.

## Optional automation

team-flow works by hand. These make it faster; set up only what you need.

| Option | What it does | Who acts |
| --- | --- | --- |
| Connectors in your agent (ClickUp, Slack, GitHub) | The agent reads tasks, channel messages and code. It creates a task, attaches a file or comments only when you tell it to. | the agent, read-only by default |
| ClickUp integrations | Slack → ClickUp: create a task from a Slack message. GitHub → ClickUp: a task ID in a branch or commit name links the commit or PR to the task. ClickUp Automations: on a status change, assign, move or notify. | ClickUp, set up by you |
| Scheduled agent | E.g. every morning the agent reads the ClickUp list and a Slack channel (read-only) and updates your `project.md`. | the agent, read-only |
| Your own flow via API (n8n, Zapier, Make, a script) | E.g. a new ClickUp task creates `tasks/CU-xxx/` with a PM file skeleton. | your flow, set up and maintained by you |

The agent never sets any of these up and never suggests an external action on its own: see [kit/RULES.md](kit/RULES.md), "Local and external".

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
