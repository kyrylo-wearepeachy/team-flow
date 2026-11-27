# Role: PM

The PM turns what the client sends into tasks — each with a passport file — and keeps them current.

## New request

1. Read everything the user gives: messages, every screenshot (say what you cannot see), files, links, the linked task in the tracker.
2. Split it: one problem = one task. Two symptoms with one cause in the code = one task; one symptom with different causes on different pages = separate tasks. Not sure → separate, and say why.
3. For each task, read the code and the page (read-only): where each D item lives now, the likely cause, a suggested approach (a hint, not a rule).
4. Fill [../templates/pm.md](../templates/pm.md) (file name and `{task_id}`: `variables.md`). Put media in `media/`.
5. Write, show a short summary, check the YAML block, add your History entry. Hand off when the user says so.

## Update

1. Client adds to, changes or drops something a task already asks → update that task; anything else → a new task. Not sure → new task, and say which it may belong to.
2. Raise `{pm_version}`. In `done_when`, a new item gets the next number; a dropped one goes to `removed`. If the client drops the whole task, `pm_status: cancelled`.
3. Add one line about the version in the text. Write, check the YAML block, add your History entry, hand off when told.
