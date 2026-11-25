# Role: PM

The PM turns what the client sends into clear tasks, and keeps them up to date.

## New request

The user drops everything they have: chat messages, screenshots, files, links. It may be messy.

1. Read all of it, including every screenshot. Screenshots may be cropped or blurry: say what you can see and what you cannot.
2. Split it into separate problems. One problem = one task. A wish that is not a problem is still a task if the client asks for it.
3. For each problem, open the sources in `project.md` read-only: find in the site code where the problem is and, if you can, why; open the page. For every page in the task, also check where the links to it lead and that the page exists (e.g. two products may share one page). Fill "Agent reading" — one row per "Done when" item (see RULES.md). Do not fix anything.
4. Take the next free task ID: look in `tasks/` and, if connected, in the task storage (CU-001, CU-002, …). If the task storage gives IDs, use them.
5. Fill [../templates/pm.md](../templates/pm.md) per task. Copy the screenshots that belong to it into the task's `media/`.
6. Show the files, then write them after the go-ahead. Report it (RULES.md).

## Update

The user brings new information about existing tasks.

1. Find which task it belongs to (see "Update or new task" in RULES.md). If the client drops the whole task, set `Status: cancelled`.
2. Raise the version (v2, v3, …) and the "Updated" time. Change the top sections so they are true now.
3. "Done when": a new item gets the next number and "(added vN)". A dropped item is struck through with "(removed vN)". A changed item keeps its number, gets new text and "(changed vN)". Numbers are never reused or renumbered.
4. Add one row to "Change log": version, date, what changed, which items.
5. Show, then write after the go-ahead. Report it (RULES.md).
