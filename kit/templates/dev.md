---
# Fill it short: one line per value, refs as file:line or a commit, evidence as a screenshot name or a few words. Details go below the block.
# task_id and pm_version come from the PM file; never type them by hand.
task_id: "{task_id}"
role: dev                    # {role}: dev, or design, content, … (any role that does the work)
by: "{nick}"
main: yes                    # {main}: yes = file {task_id}-{role}.md; no = {task_id}-{role}-{nick}.md
round: 1                     # {round}: +1 on every new round, same file
dev_status: ready_for_qa     # ready_for_qa | blocked
updated: "{now}"
pm_version: 1                # {pm_version} of the PM file you worked from
scope: all                   # {scope}: all, or [D1, D3]
items:                       # one per D item in your scope
  D1: { state: done, ref: "{file:line or commit}" }       # done needs ref
  D2: { state: blocked, why: "{what is missing}" }        # not_done / blocked need why
commit: "{branch · hash once the developer committed, or —}"
check_here: "{preview URL or page to open}"
---

# {task_id} · {role} · {nick}

Write the rest in your own words, in English: what you changed and why, the suggested commit message (`{task_id}: what changed`), what QA should look at closely, and one line per round (what changed, which QA bugs it fixes).

"done" is your claim. Only QA confirms it.
