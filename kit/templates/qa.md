---
# Fill it short: one line per value, refs as file:line or a commit, evidence as a screenshot name or a few words. Details go below the block.
# task_id and pm_version come from the PM file (always the latest); never type them by hand.
task_id: "{task_id}"
role: qa
by: "{nick}"
main: yes                    # {main}: yes = file {task_id}-qa.md; no = {task_id}-qa-{nick}.md
round: 1                     # {round}: +1 on every new round, same file
qa_result: passed            # passed | failed | blocked (no access to check)
updated: "{now}"
pm_version: 1                # {pm_version}: the latest PM version
scope: all                   # {scope}: all, or [D1, D3]
change_scope:                # read from the Dev change: check this, not the whole site
  changed: ["{file · section}"]
  may_affect: ["{page or component}"]
items:                       # one per D item in your scope
  D1: { state: pass, where: "{page · width or device}", evidence: "{screenshot or what you saw}" }   # pass needs where + evidence
  D2: { state: fail, where: "{page · width}", evidence: "{screenshot name}", bug: 1 }
  D3: { state: no_access, why: "{what access is missing}" }
bugs:
  - { id: 1, item: D2, what: "{one line}", evidence: "{screenshot name}" }
---

# {task_id} · QA · {nick}

Write the rest in your own words, in English: how you checked, anything out of scope you noticed (it does not fail the task), and one line per round.

passed = every item in scope is pass. Any fail → failed. Any no_access → blocked.
