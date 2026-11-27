<shared header: [header.md](header.md) — YAML block, title line, description. Copied from the PM file you read; the title line names your role and nick>

## QA

Updated: <YYYY-MM-DD HH:MM> · Round: <N> · By: <nick> · Main: <yes | no> · Scope: <all | D1, D2> · Result: <✅ passed | ❌ failed | blocked>

## Read

<every file of the task you read, with versions, e.g. T-001-pm.md v3, T-001-dev.md, T-001-dev-max.md>

## Change scope

What the Dev change touches, read from the code (the branch, commit or diff named in the Dev files). Check what changed and what it may affect, not the whole site.

- **Changed:** <files and sections, e.g. `css/style.css` · .btn-primary on mobile>
- **May be affected:** <pages and components that use the same code>
- **Not changed, not checked:** <the rest, in one line>

## Agent reading

| D | Checked where | Evidence | Code | Result |
| --- | --- | --- | --- | --- |
| D1 | <URL or page · device(s)> | <what you saw, and `<screenshot file>` if any> | <does the Dev change do this? ✅ matches · ❌ differs — why · — why not checked> | <✅ · ❌ · — no access> |

No ✅ without evidence. An item you could not open (no preview, no access) is `— no access`, and the Result is `blocked`, not ✅.

## Bugs

- [ ] 1. D2 · <Device>: <what is wrong — one line> — <page> — `<screenshot file>`: <one line, what it shows>

## Out of scope

- <a real problem that is not part of this task>

## Next

<→ PM (passed) | → Dev (failed) | → user: what access is missing (blocked)>

## Rounds

One row per round, newest last. The sections above always show the current state; this is the history.

| Round | Date | PM v | Dev rounds checked | Result | Bugs |
| --- | --- | --- | --- | --- | --- |
| 1 | <YYYY-MM-DD HH:MM> | <v1> | <e.g. dev 1, dev-max 1> | <✅ · ❌ · blocked> | <— or bug numbers> |

## Notes

<free space: anything about this task that has no place above, or —>
