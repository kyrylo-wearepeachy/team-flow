# team-flow — start here

This is for an AI agent. team-flow is how a team passes work: PM → Dev → QA → PM. Every person works with their own agent in their own project folder, on their own computer. Work moves between people as one file per person per task — the PM file is the task's passport — each starting with a small YAML block that a check keeps right, so every role sees the full picture: what the client asked, what changed in the code, what was checked.

The user gave you this kit, or a link to it, to set up their project folder, or to work in a folder that is already set up.

- **Language.** These instructions are in English. Talk to the user in the language they write in, short. Files you write are in English, so every teammate reads them the same way.
- **Yes.** Setting up, changing site code, and anything outside this computer need the user's explicit yes, in any language ("yes", "go", "ok", …). Your own team-flow files you just write and summarize (RULES.md, "Writing").
- **Read-only by default.** Setting up and working, you read. You write only the local files these rules name. You never act outside this folder on your own (see "Local and external" in RULES.md).

## If the user only asks what this is

Set up nothing. Answer in the user's language: translate this text closely, keep every block, and add no links, file names or paths. Keep it to one screen:

> **team-flow is a set of instructions for an AI agent, so that the PM, the developer and the QA pass tasks in one format.**
>
> **How it works:**
> 1. **The PM** gets a request from the client. The agent turns it into a task file: what to do, and how to check it is done.
> 2. **The developer** gets that file. The agent helps make the changes and writes down what changed and where in the code.
> 3. **The QA** gets both files. The agent checks the result and writes down what works and what does not.
>
> **Why:** the whole history of a task is in one place. No searching through chats, no asking again.

Then one line: "Want to set it up? Tell me your role: PM, Dev or QA."

If the user named their role, add one short paragraph: what they will do, and from whom they get files. Show the file map (step 7) and what you never do on your own only if the user asks.

## Already set up?

If the current folder has an `AGENTS.md` with a team-flow block (`# team-flow`, or a `## team-flow` section), it is set up: take the paths from its "Paths", get the rules from its "Rules" line (the team-flow MCP `rules` tool with your role, or `RULES.md` and your role file read from the link), then read the report. Do the quiet check in "Start of a session" (RULES.md), then do what the user asks.

## Set up (once per project folder)

1. **Read the kit.** Read this whole kit: through the team-flow MCP if it is connected, otherwise from the link the user gave (or the folder on disk). Do not clone or copy it: every session reads the rules from the same place again, so they are always current.
2. **Explain** in 2–3 lines what team-flow is and what you are about to do: build a small project structure locally; nothing is cloned, connected or sent.
3. **Role and nick.** If the user did not give them, ask once, in one line: the role (PM, Dev, QA, or another specialist such as design or content, who works with the Dev template) and a short nick for file names (e.g. the first letters of their name).
4. **Where to set up.** Read the current folder (only it, and its subfolders) and decide by yourself; do not ask what you can see:
   - **A project folder** (empty, or the project's files, but not itself a code repository) → set up right here, at the top level. Site code may sit in a subfolder.
   - **A general work folder** (it holds several unrelated project folders) → propose a new subfolder named after the project, e.g. `./<project>/`, as part of step 7. The user then opens the next sessions in it.
   - **A code repository** (it has `.git` and the site code) → this is the only case you ask, once: set up in the parent folder instead? Say why: here, the team-flow files would show up in the site's git.
   - **Map what already exists.** If the project already has its own structure — a folder of tasks or tickets, the site code in `src/`, `theme/` or elsewhere — point "Paths" at those folders (step 7) instead of creating new ones. Map folders only.
   - **Never write into the project's existing files.** The report is always a new file of its own: `project.md`, or `team-flow.md` if a `project.md` that is not a team-flow report already exists. Existing notes, readmes and docs stay untouched; you may read them for project facts. The only existing files you may change are `AGENTS.md`, `CLAUDE.md` and `GEMINI.md`, by adding a separate `## team-flow` section at the end.
5. **Project facts.** If the user gave a task file of this project (any role), take the project data from `project:` in its YAML block (a PM file has it): that is the team's shared data. For what is still missing, ask once, in one message: project name, the task prefix (propose one from the project name, e.g. `CS` for coffee-shop, or the prefix the task tracker already uses), site URL, preview URL, admin URL (as a link only), code repository URL, where tasks live (e.g. a ClickUp list). Unknown → `—`. Never invent.
6. **Connectors.** Ask once, in one message, which of these are connected or the user will connect, with one line each on why. Show only the rows for this role:

   | Connector | Why | PM | Dev and other specialists | QA |
   | --- | --- | --- | --- | --- |
   | Task tracker (e.g. ClickUp) | read the task files of other roles; with write access, attach your file when you ask (the PM can also create tasks) | read + write | read + write | read + write |
   | Code host (e.g. GitHub) | read the code and its recent changes, to see what is going on | read | read (or local `git log`) | read |
   | Chat (e.g. Slack) | read client messages from one channel; pasting them in chat works too | read, optional | — | — |

   If tools are already set up in your environment (a browser, a design tool, helper CLIs, connectors), say in one line which of them you will use for team-flow work and for what (see "Your own setup" in RULES.md).

   Say that read access is enough everywhere except the task tracker, where write lets you attach files on their word; that you connect nothing yourself (the user does it in their app's settings); and that everything also works without connectors (plan B: the user passes files by hand). Never ask for tokens, passwords or admin access.
   **team-flow MCP.** If it is not connected yet, add one question to the same message: "Connect team-flow directly, so the rules are always current? Say yes and I will do it." Explain in one line that without it you read the rules from the link each session, which needs web access. On yes:
   - in Claude Code, run `claude mcp add --scope user --transport http team-flow https://team-flow-mcp.kirill-264.workers.dev/mcp`;
   - in Codex, run `codex mcp add team-flow --url https://team-flow-mcp.kirill-264.workers.dev/mcp`;
   - in an app without a command line (a desktop or web app), tell the user the one step: Settings → Connectors → add a custom connector → paste `https://team-flow-mcp.kirill-264.workers.dev/mcp`.
   It works from the next session; `AGENTS.md` then names the team-flow MCP as the place of the rules. If the command fails or the user says no, `AGENTS.md` names the link.

7. **Show** what you will create, with the filled `project.md`, and wait for the yes:
   - The report (`project.md` by default) — from [templates/project.md](templates/project.md). `checked` = the `checked` of the task file you took the keys from, or now.
   - `AGENTS.md` — the shared file most agents read (Codex, Cursor, Copilot and others). It holds this block; paths are relative to this folder, defaults shown, replaced by what you mapped in step 4:
     ```text
     # team-flow
     Role: <pm|dev|qa|other role> · Nick: <nick>
     Rules: <team-flow MCP | the link you read the kit from>
     Paths:
       report: project.md
       tasks: tasks/
       code: <where the site code is, or —>
     Before any work: get the rules for your role from "Rules", then read the report.
     ```
   - Only if your own agent does not read `AGENTS.md` by itself: its own file with one import line, `@AGENTS.md` — `CLAUDE.md` for Claude, `GEMINI.md` for Gemini. Not both, not a copy.
   - A file that already exists: add your block as a separate section at the end, headed `## team-flow` (for an import file, the import line at the end), and change nothing else in it.

   Nothing else: no copy of the kit; the tasks folder appears with the first task. Leave as few traces as possible.
8. **Create** them after the yes. Tell the user in 2–3 lines: where it was set up, role, which connectors are on, what is still `—` in `project.md`. If you set up in another folder, tell the user to open the next sessions there.

## Kit updates

Nothing to do: every session reads the rules from the place named in "Rules", so changes reach everyone by themselves. If that place cannot be read (no web access, MCP not connected), tell the user and stop before any task work.
