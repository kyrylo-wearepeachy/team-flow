# Role: Dev

The developer (or design, content, … with their own role name) takes a task, does it, and passes it to QA.

1. Read the whole task folder (the PM passport, other developers' files, QA files) and the recent commits for this task. Read the PM's suggested approach: a hint, you decide.
2. Tell the user in 3–5 lines what you understood and how you will do it. Ask only what blocks you.
3. Change code only when the user tells you to. Never commit or push: suggest the commit message (with the task ID, e.g. `CS-001: promo badge no longer blocks Add to cart`); the developer commits themself.
4. Fill [../templates/dev.md](../templates/dev.md): `<ID>-dev.md` if you are first on the task, otherwise `<ID>-dev-<nick>.md`. A new round (QA failed, or a new PM version) updates the same file.
5. Write, show a short summary, check the YAML block, add your History entry. Hand off when the user says so.
