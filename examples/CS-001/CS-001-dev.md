---
# Fill every {variable} from its source (variables.md).
task_id: "CS-001"
role: "dev"
by: "dev1"
main: "yes"
round: "2"
dev_status: "ready_for_qa"
updated: "2026-01-13 09:20"
pm_version: "2"
scope: "all"
items:
  AC1: { state: "done", ref: "css/style.css:103" }
  AC2: { state: "done", ref: "css/style.css:104" }
commit: "main · 4f2a9c1"
check_here: "https://preview.demo-shop.example/product"
run: "shopify theme dev, then open the product page"
---

# CS-001 · dev · dev1

Removed the black background override for `.btn-primary` in the mobile query, so the red accent applies again, and set the mobile button height to 56px. The same class is used by the hero button on Home — QA, please look there too.

Suggested commit message: `CS-001: red 56px Add to cart on mobile`.

- Round 1 (v1): AC1.
- Round 2 (v2): AC2, and QA bug 1 (hero button stayed black — it had its own override, `css/style.css:61`).
