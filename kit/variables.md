# team-flow variables

One system. Every `{name}` in this kit is a variable from this list. Each value lives in **one** place (its source). Everywhere else it is only used: when you write a file, fill each `{name}` from its source — never type a copied value by hand, never leave `{…}` in a written file. If a source changes, the copies follow the next time a file is written.

## Kit

Values are here, nowhere else.

| Variable | Value |
| --- | --- |
| `{kit_repo}` | `https://github.com/kyrylo-wearepeachy/team-flow` |
| `{mcp_url}` | `https://team-flow-mcp.kirill-264.workers.dev/mcp` |

## Person — source: `AGENTS.md` (template [templates/agents-block.md](templates/agents-block.md))

| Variable | Meaning |
| --- | --- |
| `{role}` | `pm`, `dev`, `qa`, or another role (design, content, …) |
| `{nick}` | the person's short name for file names |
| `{rules}` | where the rules are read from: `team-flow MCP` or `{kit_repo}` |
| `{report}` | path of the project report, default `project.md` |
| `{tasks}` | path of the tasks folder, default `tasks/` |
| `{code}` | path of the site code, or `—` |

## Project — source: the project card, i.e. the YAML block of `{report}` (template [templates/project.md](templates/project.md))

| Variable | Meaning |
| --- | --- |
| `{project}` | project name |
| `{task_prefix}` | letters of task IDs, e.g. `CS` |
| `{repository}` | code repository URL, or `—` |
| `{site}` | live site URL, or `—` |
| `{preview}` | preview URL, or `—` |
| `{admin}` | admin URL (link only), or `—` |
| `{task_storage}` | task tracker list URL (e.g. ClickUp), or `—` |
| `{project_card}` | where the team shares the project card once: a link to a pinned tracker task or the list description; or `—` (then the card is passed by hand once) |

The project card is the one shared place for these. Nothing copies them: the story only links `{project_card}` and `kit: {kit_repo}`, so a newcomer with one task file opens the card and has every current link.

## Task — source: the YAML block of the story (the PM file) (template [templates/pm.md](templates/pm.md))

| Variable | Meaning |
| --- | --- |
| `{task_id}` | `{task_prefix}-` + the next free three-digit number (or the tracker's own ID) |
| `{pm_version}` | 1, +1 on every change |
| `{pm_status}` | `ready_for_dev` · `needs_client_answer` · `cancelled` |
| `{type}` | `bug` · `change` · `content` · `new_feature` |
| `{devices}` | list of `all` · `desktop` · `tablet` · `mobile` |
| `{title}` | `[Page] what to do`, up to 8 words |
| `{page}` · `{url}` · `{design}` | page name, page URL, design link (or `—`) |
| `AC1`, `AC2`, … | acceptance criteria: each one checkable result; numbers never change or get reused |
| `{depends_on}` | task IDs this one waits for, e.g. `[CS-003]`, or `[]` |

Every other file of the task copies `{task_id}` and `{pm_version}` from the PM file.

## Person in a task — source: your own task file (templates [dev.md](templates/dev.md), [qa.md](templates/qa.md))

| Variable | Meaning |
| --- | --- |
| `{main}` | `yes` for the first person on a role, `no` for anyone who joins later |
| `{round}` | 1, +1 on every new round, same file |
| `{dev_status}` | `ready_for_qa` · `blocked` |
| `{qa_result}` | `passed` · `failed` · `blocked` |
| `{scope}` | `all`, or the acceptance criteria you take, e.g. `[AC1, AC3]` |
| `{now}` | the time you write, `YYYY-MM-DD HH:MM` |
| `{run}` | developers only, in the dev file: how to run the site for development — a local command or short steps, no secrets. Take it from an earlier dev file of the project if there is one. |
| `{dev_state}` | a developer's acceptance criterion: `done` (needs `{ref}`) · `not_done` · `blocked` (both need `{why}`). |
| `{qa_state}` | a QA acceptance criterion: `pass` (needs `{where}` and `{evidence}`) · `fail` (needs a bug number) · `no_access` (needs `{why}`) |
| `{ref}` | `file:line` or a commit hash |
| `{why}` | what is missing, a few words |
| `{where}` | page and width or device, e.g. `product · 390` |
| `{evidence}` | a screenshot file name, or a few words of what you saw |
| `{commit}` | `branch · hash` once the developer committed, or `—` |

Rules for `{qa_result}`: `passed` only if every item in scope is `pass`; any `fail` → `failed`; any `no_access` → `blocked`.

Values: one line each. A acceptance criterion is a checkable result in up to 10 words. Explanations go below the YAML block, never into it.

## Built from variables

| What | Pattern |
| --- | --- |
| task folder | `{tasks}/{task_id}/` |
| PM file | `{tasks}/{task_id}/{task_id}-pm.md` |
| your file (main) | `{tasks}/{task_id}/{task_id}-{role}.md` |
| your file (joined later) | `{tasks}/{task_id}/{task_id}-{role}-{nick}.md` |
| media | `{tasks}/{task_id}/media/{task_id}-short-name.png` (a file the user adds keeps its name) |
| branch name (suggested) | `{task_id}-short-name` |
| commit message (suggested) | `{task_id}: what changed` — the developer commits; agents never commit or push |
| History entry | see below |

### History entry

One per task file you write, at the end of History in `{report}`, never edited later:

```text
### {now} · {task_id} · {role} · round {round} · PM v{pm_version}
Task:    {title}
Done:    what you did, one or two lines (PM: what the client asked · developer: what changed and where · QA: what was checked and the result)
Content: what it came from: client message (date, a few words), files, design links
Links:   commit, tracker task, related tasks ("continues {task_id}")
```

### Optional, later

Some trackers link code to a task by its ID: with ClickUp's GitHub integration, a ClickUp task ID in a branch name, commit message or pull request title links it to the task. If the team sets `{task_prefix}` to the tracker's custom task ID prefix, the suggested branch and commit names above link by themselves. team-flow does not set this up.
