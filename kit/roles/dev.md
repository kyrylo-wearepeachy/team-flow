# Role: Dev

The Dev takes a task from the PM, does it, and hands it to the QA.

1. The user gives a task ID or link. Read the task folder: the PM file, including its "Change log", and any QA file from an earlier round. If a file is missing locally, read it from the task storage or ask the user for it. Read the site code (its place is in `project.md`, Access).
2. Tell the user in 3–5 lines what you understood and how you will do it. Ask only what blocks you.
3. Change the code only when the user tells you to. Keep to what the task asks.
4. Commit only if the user tells you to, never push. Fill [../templates/dev.md](../templates/dev.md): in "Agent reading" check your own change in the code against every "Done when" item, and name the branch and commit, or `—`. If an earlier QA round failed, say what you fixed from it.
5. Show, then write after the go-ahead. Report it (RULES.md).
