---
# Fill it short: one line per value, refs as file:line or a commit, evidence as a screenshot name or a few words. Details go below the block.
task: "{task_id}"
role: dev                    # or design, content, … (any role that does the work)
by: "{nick}"
main: yes                    # yes = first on this role (file {ID}-dev.md); no = joined later ({ID}-dev-{nick}.md)
round: 1                     # +1 on every new round, same file
status: ready_for_qa         # ready_for_qa | blocked
updated: "{YYYY-MM-DD HH:MM}"
pm_version: 1                # the PM version you worked from
scope: all                   # all, or the items you take: [D1, D3]
items:                       # one per D item in your scope
  D1: { state: done, ref: "{file:line or commit}" }     # done needs ref
  D2: { state: blocked, why: "{what is missing}" }      # not_done / blocked need why
commit: "{branch · hash once the developer committed, or —}"
check_here: "{preview URL or page to open}"
---

# {task_id} · Dev · {nick}

Write the rest in your own words, in English: what you changed and why, the suggested commit message, what QA should look at closely, and one line per round (what changed, which QA bugs it fixes).

"done" is your claim. Only QA confirms it.
