---
# Fill it short: one line per value, refs as file:line or a commit, evidence as a screenshot name or a few words. Details go below the block.
task: "{task_id}"
role: qa
by: "{nick}"
main: yes                    # yes = first QA on this task (file {ID}-qa.md); no = joined later ({ID}-qa-{nick}.md)
round: 1                     # +1 on every new round, same file
result: passed               # passed | failed | blocked (no access to check)
updated: "{YYYY-MM-DD HH:MM}"
pm_version: 1                # the PM version you checked against (always the latest)
scope: all                   # all, or [D1, D3]
change_scope:                # read from the Dev change: check this, not the whole site
  changed: ["{file · section}"]
  may_affect: ["{page or component}"]
items:                       # one per D item in your scope
  D1: { state: pass, where: "{page · width/device}", evidence: "{screenshot or what you saw}" }   # pass needs where + evidence
  D2: { state: fail, where: "{page · width}", evidence: "{…}", bug: 1 }
  D3: { state: no_access, why: "{what access is missing}" }
bugs:
  - { id: 1, item: D2, what: "{one line}", evidence: "{screenshot}" }
---

# {task_id} · QA · {nick}

Write the rest in your own words, in English: how you checked, anything out of scope you noticed (it does not fail the task), and one line per round.

passed = every item in scope is pass. Any fail → failed. Any no_access → blocked.
