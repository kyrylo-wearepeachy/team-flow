---
# Task story: the source of the task variables. Fill every {variable} from its source (variables.md).
task_id: "CS-001"
role: pm
by: "pm1"
pm_version: "2"
pm_status: "ready_for_dev"
updated: "2026-01-12 16:05"
type: "bug"
devices: [mobile]
title: "[Product] Make Add to cart red on mobile"
page: "Product"
url: "https://demo-shop.example/product"
design: "—"
acceptance_criteria:
  AC1: "Add to cart is red on mobile"
  AC2: "Add to cart is 56px tall on mobile"
removed: []
depends_on: []
project_card: "https://app.clickup.com/t/0000"
kit: "https://github.com/kyrylo-wearepeachy/team-flow"
---

# CS-001 · PM · pm1

**What the client wants:** on phones the Add to cart button is black; it should be red like on desktop, and a bit bigger.

**What the agent found:** AC1 — `css/style.css:103`, `.btn-primary { background: #111 }` inside the mobile media query overrides the red accent. AC2 — `css/style.css:104` sets no height; the button is about 44px.

**Suggested approach (not binding):** drop the background override on line 103; set the mobile height next to it.

**Materials:** `IMG_4821.png` — phone screenshot of the product page, black button, cropped at the bottom.

**Versions:** v1 — AC1. v2 — the client asked for a bigger button: AC2 added.
