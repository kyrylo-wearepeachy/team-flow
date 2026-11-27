---
# Fill every {variable} from its source (variables.md).
task_id: "{task_id}"
role: qa
by: "{nick}"
main: "{main}"
round: "{round}"
qa_result: "{qa_result}"
updated: "{now}"
pm_version: "{pm_version}"
scope: "{scope}"
change_scope:
  changed: ["{file · section}"]
  may_affect: ["{page or component}"]
items:
  D1: { state: "{qa_state}", where: "{where}", evidence: "{evidence}" }
bugs:
  - { id: 1, item: D1, what: "{one line}", evidence: "{evidence}" }
---

# {task_id} · QA · {nick}

Your own words, in English: how you checked · anything out of scope you noticed (it does not fail the task) · one line per round.
