---
# The task's passport and the source of the task variables (variables.md). Only its author changes it.
# Fill it short: one line per value, D items up to 10 words, details go below the block.
task_id: "{task_id}"
role: pm
by: "{nick}"
pm_version: 1                # {pm_version}: +1 on every change
pm_status: ready_for_dev     # ready_for_dev | needs_client_answer | cancelled
updated: "{now}"
type: bug                    # bug | change | content | new_feature
devices: [all]               # all | desktop | tablet | mobile
title: "{title}"
page: "{page}"
url: "{url}"
design: "{design}"
done_when:                   # numbers never change or get reused
  D1: "{one checkable result}"
  D2: "{one checkable result}"
removed: []                  # D numbers dropped in later versions, e.g. [D3]
project:                     # filled from {report}, never typed by hand
  project: "{project}"
  task_prefix: "{task_prefix}"
  repository: "{repository}"
  site: "{site}"
  preview: "{preview}"
  admin: "{admin}"
  task_storage: "{task_storage}"
---

# {task_id} · PM · {nick}

Write the rest in your own words, in English. What usually helps the next roles:

- **What the client wants** — 1–3 sentences, as of this version.
- **What the agent found** — per D item, where it lives in the code now (`file:line`), or "not found", or why not checked.
- **Suggested approach (not binding)** — the likely cause and what could change. A hint; the developer decides.
- **Materials** — each file by name, one line on what it shows.
- **Questions for the client** — only what blocks the work.
- **Versions** — one line per version: what changed, which D items.
