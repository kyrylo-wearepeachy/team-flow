# team-flow — start here

This is for an AI agent. team-flow is how a team passes work: PM → Dev → QA → PM. Every person works with their own agent in their own project folder, on their own computer. Work moves between people as one file per role per task, all with the same header, so every role sees the full picture: what the client asked, what changed in the code, what was checked.

The user gave you this kit, or a link to it, to set up their project folder, or to work in a folder that is already set up.

- **Language.** These instructions are in English. Talk to the user in the language they write in, short. Files you write are in English, so every teammate reads them the same way.
- **Go-ahead.** Wherever these rules say "go-ahead", it means the user's explicit yes to that step, in any language ("yes", "go", "ok", …). Without it, write nothing.
- **Read-only by default.** Setting up and working, you read. You write only the local files these rules name. You never act outside this folder on your own (see "Local and external" in RULES.md).

## Already set up?

If the current folder has `project.md` and an agent instructions file (`CLAUDE.md`, `AGENTS.md` or `GEMINI.md`) with a `team-flow role:` line, it is set up: read `RULES.md` and your role file from the local kit copy named there, then `project.md`. Do the quiet check in "Start of a session" (RULES.md), then do what the user asks.

## Set up (once per project folder)

1. **Read the kit.** Read this whole kit: from the link the user gave, or from the folder on disk. Do not clone anything.
2. **Explain** in 2–3 lines what team-flow is and what you are about to do: build a small project structure locally; nothing is cloned, connected or sent.
3. **Role and nick.** If the user did not give them, ask once, in one line: the role (PM, Dev, QA, or another specialist such as design or content, who works with the Dev template) and a short nick for file names (e.g. `anna`).
4. **Where to set up.** Read the current folder (only it, and its subfolders) and decide by yourself; do not ask what you can see:
   - **A project folder** (empty, or the project's files, but not itself a code repository) → set up right here, at the top level. Site code may sit in a subfolder.
   - **A general work folder** (it holds several unrelated project folders) → propose a new subfolder named after the project, e.g. `./<project>/`, as part of step 7. The user then opens the next sessions in it.
   - **A code repository** (it has `.git` and the site code) → this is the only case you ask, once: set up in the parent folder instead? Say why: here, the team-flow files would show up in the site's git.
   - Note what you found: where the site code is, an existing `project.md`, `tasks/`, task files.
5. **Project facts.** If the user gave a task file of this project (any role), take the project keys from the YAML block of its header: that is the team's shared data. For what is still missing, ask once, in one message: project name, site URL, preview URL, admin URL (as a link only), code repository URL, where tasks live (e.g. a ClickUp list). Unknown → `—`. Never invent.
6. **Connectors.** Ask once, in one message, which of these are connected or the user will connect, with one line each on why. Show only the rows for this role:

   | Connector | Why | PM | Dev and other specialists | QA |
   | --- | --- | --- | --- | --- |
   | Task tracker (e.g. ClickUp) | read tasks and the task files of other roles | read | read | read |
   | Code host (e.g. GitHub) | read the site code when it is not in this folder | read | — (code is local) | read |
   | Chat (e.g. Slack) | read client messages from one channel; pasting them in chat works too | read, optional | — | — |

   Say that read access is enough, that you connect nothing yourself (the user does it in their app's settings), and that everything also works without connectors: the user then passes files by hand. Never ask for tokens, passwords, admin access or write access.
7. **Show** what you will create, with the filled `project.md`, and wait for the go-ahead:
   - `project.md` — from [templates/project.md](templates/project.md). `checked` = the `checked` of the task file you took the keys from, or now.
   - `.team-flow/` — a local copy of this kit's files (`START.md`, `RULES.md`, `roles/`, `templates/`), exactly as read.
   - **One** agent instructions file, the one your agent reads (`CLAUDE.md` for Claude, `GEMINI.md` for Gemini, `AGENTS.md` for others), with exactly these lines:
     ```text
     team-flow role: <pm|dev|qa|other role> · nick: <nick>
     team-flow kit: .team-flow/ (source: <link or path you read the kit from>)
     Before any work: read .team-flow/RULES.md and .team-flow/roles/<role>.md, then project.md here.
     ```
     If that file exists, add the lines at the top and change nothing else.

   Nothing else: `tasks/` appears with the first task. Leave as few traces as possible.
8. **Create** them after the go-ahead. Tell the user in 2–3 lines: where it was set up, role, which connectors are on, what is still `—` in `project.md`. If you set up in another folder, tell the user to open the next sessions there.

## Kit updates

Only when the user asks: read the kit again from the source in your agent instructions file, show what changed, and replace `.team-flow/` after the go-ahead.
