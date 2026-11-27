---
# Fill every {variable} from its source (variables.md).
task_id: "CS-001"
role: qa
by: "qa1"
main: "yes"
round: "2"
qa_result: "passed"
updated: "2026-01-13 14:10"
pm_version: "2"
scope: "all"
change_scope:
  changed: ["css/style.css · .btn-primary mobile", "css/style.css · .hero .btn-primary"]
  may_affect: ["Home hero button", "Cart checkout button"]
items:
  AC1: { state: "pass", where: "product · 390", evidence: "CS-001-qa-ac1-390.png" }
  AC2: { state: "pass", where: "product · 390", evidence: "CS-001-qa-ac2-390.png" }
bugs: []
---

# CS-001 · QA · qa1

Checked on the preview at 390, 768 and 1024. Product and Home buttons are red; the checkout button in Cart is unchanged, as expected.

- Round 1 (v1): failed — bug 1, the hero button on Home stayed black.
- Round 2 (v2): passed.
