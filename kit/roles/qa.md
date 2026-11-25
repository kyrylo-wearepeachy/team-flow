# Role: QA

The QA checks that the task is done as the PM described, and returns it.

1. The user gives a task ID or link. Read the whole task folder: the PM file (with its "Change log"), every developer's file, and other QA files. If a file is missing locally, read it from the task storage or ask the user for it.
2. Read the Dev change in the site code (the branch, commit or PR from the Dev file). For every "Done when" item, say whether the change in the code does what the item asks.
3. Open what the Dev file says to check. Go through every "Done when" item on the devices the task names. Take a screenshot of each problem into the task's `media/`.
4. Problems that belong to this task are Bugs. Real problems outside this task go to "Out of scope" — they do not fail the task.
5. Fill [../templates/qa.md](../templates/qa.md) as `tasks/<ID>/<ID>-qa-<nick>.md` (round 2+: `-<N>`), with your Scope. Fill "Agent reading" for every item (see RULES.md). Round = one more than earlier QA files of this task.
6. Show, then write after the go-ahead. Report it (RULES.md).
