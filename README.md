# team-flow

**team-flow is a set of instructions for an AI agent, so that the PM, the developer and the QA pass tasks in one format.**

1. **The PM** gets a request from the client. The agent turns it into a task file: what to do, and how to check it is done.
2. **The developer** gets that file. The agent helps make the changes and writes down what changed and where in the code.
3. **The QA** gets both files. The agent checks the result and writes down what works and what does not.

**Why:** the whole history of a task is in one place. No searching through chats, no asking again.

**Team hub:** [team-flow-hub.teamflowkit.workers.dev](https://team-flow-hub.teamflowkit.workers.dev) — the guide, a shared file space with private links, and Support.

> **AI agent reading this:** to explain it, use the short text above. To set it up, follow [kit/START.md](kit/START.md).

## Get started

Open your project folder in your AI agent (Claude, Codex, Cursor, Gemini, …) and paste, in any language:

> https://github.com/kyrylo-wearepeachy/team-flow — set up team-flow, I'm the PM

(or Dev, or QA). The agent:

- explains in a few lines what it is about to do;
- looks around your folder by itself (site code, existing tasks);
- asks once for your nick, the missing project links and which tools you have connected (task tracker, code host, chat) — read access is enough;
- offers to connect team-flow directly, so the rules stay current — just say yes;
- shows what it will create and writes nothing without your yes.

Your role and nick are asked once. Every later session takes them from `AGENTS.md`.

### Connect by hand

The agent offers this itself. To do it yourself, add the team-flow MCP server:

| Agent | How |
| --- | --- |
| Claude Code | `claude mcp add --transport http team-flow https://team-flow-mcp.teamflowkit.workers.dev/mcp` |
| Codex | `codex mcp add team-flow --url https://team-flow-mcp.teamflowkit.workers.dev/mcp` |
| Claude desktop / web | Settings → Connectors → Add custom connector → `https://team-flow-mcp.teamflowkit.workers.dev/mcp` |
| Gemini CLI | `settings.json`: `"mcpServers": { "team-flow": { "httpUrl": "https://team-flow-mcp.teamflowkit.workers.dev/mcp" } }` |

## What appears in your folder

```text
AGENTS.md       your role, your nick, where the rules are
project.md      the project links and your own History
tasks/CS-001/   the task's files: yours and the ones others pass you
```

Claude and Gemini also get a one-line `CLAUDE.md` or `GEMINI.md` that points to `AGENTS.md`. If your project already has its own folders for tasks or code, the agent uses them instead of creating new ones. The rules themselves are not copied: they are read fresh every session.

## How a task moves

| Step | Who | File | What is in it |
| --- | --- | --- | --- |
| 1 | PM | `CS-001-pm.md` — the story | what to do, acceptance criteria (`AC1`, `AC2`…), where it lives in the code, a suggested approach |
| 2 | Developer | `CS-001-dev.md` | per criterion: done (with `file:line`) or blocked (with why); the suggested commit message |
| 3 | QA | `CS-001-qa.md` | what changed, and per criterion: pass (with evidence), fail (with a bug) or no access |
| back | Developer, QA | same files | a new round updates the same file and adds one line about the round |

Every file starts with a short YAML table — the same shape for everyone — and below it each person writes in their own words. A second developer or QA on the task adds their own file (`CS-001-dev-<nick>.md`). Each person also keeps a short History in `project.md`, so a year later anyone can find what was done, when and from what.

A finished example is in [examples/](examples/).

## Commands

With team-flow connected, each step is a ready command in your agent (in Claude Code: the `/` menu). Without it, say the same in words.

| Role | Command | When |
| --- | --- | --- |
| PM | `pm_new_request` | the client sent something: make tasks |
| PM | `pm_update_task` | the client changed or added something |
| Dev | `dev_take_task` | take a task |
| Dev | `dev_new_round` | QA returned it, or the PM updated it |
| QA | `qa_check_task` | check a task, with evidence |
| QA | `qa_visual_check` | compare the site with the design (e.g. Figma) |
| QA, Dev | `qa_responsive_view` | one page at 390 · 768 · 1024 · 1440 side by side |
| Anyone | `project_status` | what is going on: every task, who waits for whom |
| Anyone | `task_draft` | a quick task file from a sentence, a link or a screenshot |
| Anyone | `find_cause` | the likely cause of a problem, from the page, the design and the code |
| Anyone | `handoff` | you are done: what to pass on, and to whom |
| Anyone | `validate_task_file` | check your file before you pass it on |
| Anyone | `share_text` | save a log or a note as a private link for a task file |
| Anyone | `suggest_change` · `send_feedback` | propose a change to team-flow and send it to the kit owner |

## Team hub

[team-flow-hub.teamflowkit.workers.dev](https://team-flow-hub.teamflowkit.workers.dev)

- **Guide** — what team-flow is, how to install it, what to ask your agent.
- **Files** — folders, uploads up to 10 MB, quick text files, a link for each file.
- **Private links** — not listed anywhere, only the link opens the file, gone after 1, 7 or 30 days. Agents use them for screenshots and logs in task files.
- **Trash** — things wait 7 days, or you delete them now. Everything moves to Trash after 30 days.
- **Support** — questions and ideas go to the kit owner. Agents can send them too (`send_feedback`).

No passwords, keys or private client data in the hub.

## What is inside

```text
kit/
├── START.md        setup, and what to do at the start of every session
├── RULES.md        how every role works: files, hand-off, writing, history, never
├── variables.md    every {variable}: its meaning, allowed values and the one place its value lives
├── actions.md      task draft, find the cause, visual check, responsive view, share content
├── roles/          pm.md · dev.md · qa.md — the steps of each role
└── templates/      pm.md · dev.md · qa.md · project.md · agents-block.md
examples/           one finished task, for reference
```

Change a value in one place (`variables.md` or a template) and every agent picks it up in its next session.

## Good to know

- **Early version.** Tested only on a demo site so far. Tell us what breaks: Support in the hub, or ask your agent to `send_feedback`.
- **The story is the source.** Its "Suggested approach" is only a hint: the developer decides. A developer's "done" is a claim; only QA confirms it.
- **Files move** through a connected task tracker (e.g. ClickUp) when you ask your agent to attach them, or by hand. Nothing syncs on its own.
- **The agent reads by default.** It writes only your own team-flow files and shows a short summary. It asks for a yes before code changes and anything outside your computer, and it never commits, pushes or posts on its own.
- **Free.** The server and the hub run on free plans; nothing to buy.
