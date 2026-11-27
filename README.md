# team-flow

**team-flow is a set of instructions for an AI agent, so that the PM, the developer and the QA pass tasks in one format.**

1. **The PM** gets a request from the client. The agent turns it into a task file: what to do, and how to check it is done.
2. **The developer** gets that file. The agent helps make the changes and writes down what changed and where in the code.
3. **The QA** gets both files. The agent checks the result and writes down what works and what does not.

**Why:** the whole history of a task is in one place. No searching through chats, no asking again.

> **AI agent reading this:** to explain it, use the short text above. To set it up, follow [kit/START.md](kit/START.md).

## Get started

Open your project folder in your AI agent and paste, in any language:

> https://github.com/kyrylo-wearepeachy/team-flow — set up team-flow, I'm the PM

(or Dev, or QA). The agent asks a few short questions, offers to connect team-flow directly so the rules stay current (just say yes), and writes nothing without your yes.

## What appears in your folder

```text
AGENTS.md      your role, your nick, where the rules are
project.md     your mini report: tasks and a log
tasks/CU-001/  the task's files: yours and the ones others pass you
```

Claude and Gemini also get a one-line `CLAUDE.md` or `GEMINI.md` that points to `AGENTS.md`. The rules themselves are not copied: they are read fresh every session.

## Commands

With team-flow connected, each step is a ready command in your agent (in Claude Code: the `/` menu). Without it, just say the same in words.

| Role | Command | When |
| --- | --- | --- |
| PM | `pm_new_request` | the client sent something: make tasks |
| PM | `pm_update_task` | the client changed or added something |
| Dev | `dev_take_task` | take a task |
| Dev | `dev_new_round` | QA returned it, or the PM updated it |
| QA | `qa_check_task` | check a task, with evidence |
| Anyone | `project_status` | what is going on in the project |
| Anyone | `handoff` | you are done: what to pass on, and to whom |
| Anyone | `suggest_change` | propose a change to team-flow |

## Good to know

- **Early version.** Tested only on a demo site so far. Tell us what breaks.
- **Files move by hand** or through a connected task tracker (e.g. ClickUp) when you tell your agent to. Nothing syncs on its own.
- **The agent reads by default** and writes only your own local files, after your yes. It never sends, posts or pushes on its own.
- **To suggest a change**, ask your agent (`suggest_change`): it drafts a short proposal, and you open it as an issue here or send it to the kit owner.
