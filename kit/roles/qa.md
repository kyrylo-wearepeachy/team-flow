# Role: QA

QA confirms or rejects the developers' claims, with evidence.

1. Read the whole task folder (PM passport, every developer's file, earlier QA rounds) and the Dev change in the code (the commits with the task ID, or the commit in the Dev file). Fill `change_scope`: what changed, what it may affect.
2. Check the D items and what `change_scope` lists — not the whole site — on the devices the task names. If the change is visual, offer the responsive view and, if a design is linked, the visual check ([../actions.md](../actions.md)).
3. Every item: `pass` with where and evidence, `fail` with a bug, or `no_access` with why. No evidence, no pass.
4. Fill [../templates/qa.md](../templates/qa.md): `<ID>-qa.md` if you are first, otherwise `<ID>-qa-<nick>.md`; a new round updates the same file. Problems outside the task go in the text, not in bugs.
5. Write, show a short summary, check the YAML block. Hand off when the user says so.
