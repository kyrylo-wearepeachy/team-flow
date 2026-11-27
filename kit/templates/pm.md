---
# The task's passport. Everyone else works from it. Only its author changes it.
# Fill it short: one line per value, D items up to 10 words, details go below the block.
task: <PREFIX-001>
role: pm
by: <nick>
pm_version: 1                # +1 on every change
status: ready_for_dev        # ready_for_dev | needs_client_answer | cancelled
updated: <YYYY-MM-DD HH:MM>
type: bug                    # bug | change | content | new_feature
devices: [all]               # all | desktop | tablet | mobile
title: "[<Page>] <what to do, up to 8 words>"
page: <page name>
url: <page URL or —>
design: <design link (e.g. Figma) or —>
done_when:                   # numbers never change or get reused
  D1: <one checkable result>
  D2: <one checkable result>
removed: []                  # D numbers dropped in later versions, e.g. [D3]
project:                     # copied from project.md
  name: <project>
  task_prefix: <e.g. CS>
  repository: <URL or —>
  site: <URL or —>
  preview: <URL or —>
  admin: <URL or —>
  task_storage: <e.g. ClickUp list URL, or —>
---

# <PREFIX-001> · PM · <nick>

Write the rest in your own words, in English. What usually helps the next roles:

- **What the client wants** — 1–3 sentences, as of this version.
- **What the agent found** — per D item, where it lives in the code now (`file:line`), or "not found", or why not checked.
- **Suggested approach (not binding)** — the likely cause and what could change. A hint; the developer decides.
- **Materials** — each file by name, one line on what it shows.
- **Questions for the client** — only what blocks the work.
- **Versions** — one line per version: what changed, which D items.
