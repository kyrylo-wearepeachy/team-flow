# Role: QA

The QA checks that the task is done as the PM described, and returns it.

1. The user gives a task ID or link. Read the whole task folder: the PM file (with its "Change log"), every developer's file, and other QA files. If a file is missing locally, read it from the task storage or ask the user for it.
2. Read the Dev change in the site code (the branch, commit or diff from the Dev files) and fill "Change scope": what changed, what it may affect, what did not change. Check those and the "Done when" items, not the whole site. For every item, say whether the change in the code does what it asks.
3. Open what the Dev file says to check (a preview or the site). Without access to it, say so: the result is `blocked`. Go through every "Done when" item on the devices the task names. Take a screenshot of each problem into the task's `media/`.
4. Problems that belong to this task are Bugs. Real problems outside this task go to "Out of scope" — they do not fail the task.
5. Fill [../templates/qa.md](../templates/qa.md) as `tasks/<ID>/<ID>-qa.md` if you are the first QA on the task (`Main: yes`), otherwise `<ID>-qa-<nick>.md` (`Main: no`); a new round updates the same file and adds a row to Rounds. Name your Scope. Fill "Agent reading" for every item (see RULES.md), with where you checked and the evidence: no ✅ without it, and no access means `blocked`.
6. Show, then write after the go-ahead. Report it (RULES.md).
