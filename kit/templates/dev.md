<shared header: [header.md](header.md) — YAML block, title line, description. Copied from the PM file you read; the title line names your role and nick>

## <Dev | other role>

Updated: <YYYY-MM-DD HH:MM> · Round: <N> · By: <nick> · Main: <yes | no> · Scope: <all | D1, D2> · Status: <ready_for_qa | blocked>

## Read

<every file of the task you read, with versions, e.g. CU-001-pm.md v3, CU-001-dev.md, CU-001-qa.md (bugs 1, 2)>

## Done

<1–3 lines: what is changed now, over all rounds, in terms the QA can see.>

## Agent reading

| D | What I did | Changed in | Code |
| --- | --- | --- | --- |
| D1 | <the change, in terms the QA can see> | <`file:line`> | <✅ matches · ❌ differs — why · — why not checked> |

## Check here

<preview URL or page to open>

## Not done

- <"Done when" items not done, by number (D2), risks, what to look at closely>

## Commit

<branch · commit hash or PR URL · commit message, or —>

## Rounds

One row per round, newest last. The sections above always show the current state; this is the history.

| Round | Date | PM v | What changed in this round | Fixed QA bugs |
| --- | --- | --- | --- | --- |
| 1 | <YYYY-MM-DD HH:MM> | <v1> | <one line, `file:line`> | <— or bug numbers> |

## Notes

<free space: anything about this task that has no place above, or —>
