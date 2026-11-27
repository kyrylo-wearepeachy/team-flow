# team-flow actions (any role)

Common actions any role can ask for. Each one: work out by yourself which of your tools fit (browser, design access, code access, connectors), say in one line what you will use and what you propose, and act after the user's yes. If a tool is missing, say what you would need and offer the simplest way around it (e.g. screenshots from the user). Never set up a tool yourself.

## Task draft

A quick task file from anything: one sentence, a link, a screenshot.

1. Read what the user gave. If it is a link to a task tracker task and the tracker is connected, read the task, its comments and attachments.
2. Fill the PM template as far as the facts go: the YAML block with one or more `acceptance_criteria` items, and in the text the materials with one line each. Unknown → `—`; open points go to the questions for the client.
3. Take the next ID with the project's `task_prefix`.
4. Write, show a short summary, validate the file. The PM file is the task's story; a non-PM author is named in `by`.

## Find the cause

The likely cause of a problem, before anyone fixes it.

1. Look at every source you can reach: the page (in a browser, at the width where it breaks), the design if one is linked, the screenshots, the site code.
2. Narrow it down: the element, its styles or script, the line that makes it behave so.
3. Answer in 3-5 lines: "Most likely: the cause, `file:line`, because of what you saw." Add what else it could be, and how sure you are.
4. Read-only. If a task exists, offer to put it into the PM file's "Suggested approach" or into your own file's Notes.

## Visual check

Compare the site with the design, for the pages in the task's "Change scope".

1. Find the design: a link in the PM file (e.g. Figma) or design files the user gave. If you can read the design (a connector or design tool you have), take the frames for the same pages and widths. If not, ask the user for screenshots of the frames.
2. Open each page at the frame's width (see "Responsive view").
3. Compare what matters for the task: layout, spacing, sizes, colours, texts. Ignore what is out of scope.
4. Write each difference as one line with the width and a screenshot pair (site · design). In a QA file they go to the item's `evidence`, or to `bugs`.

## Responsive view

One page at several widths side by side, all at the same height: 390 · 768 · 1024 · 1440 by default.

- Pick the way yourself from what your environment allows, and say in one line what you propose. Usually: set each width in your browser in turn, take a screenshot, and show the screenshots side by side. Frames often fail (sites forbid being shown in a frame), so try them only if you know the site allows it.
- Never install anything for it; if the best way needs something new, describe it and let the user decide.
- Look for: overflow and sideways scroll, wrapped or cut text, overlapping elements, hidden or misplaced buttons, image cropping.

## Task context

Before you work on a task. Read only.

1. **Task files:** every file in `{tasks}/{task_id}/` — the story (the PM file) and every other person's file. Read the YAML first, then the text.
2. **Task tracker:** if connected, the latest files and comments of the task there. If newer than the local ones, say so.
3. **Code changes:** commits and pull requests that name `{task_id}`, and what they changed.
4. **History:** entries for `{task_id}`, or "continues `{task_id}`", in `{report}`.

Then tell the user in 3–5 lines: what the task asks now (`{pm_version}`), who claimed what, what QA confirmed, what is open, what you will do next.

## Project status

What is going on in the project. Read only.

1. For each task folder in `{tasks}` (and the tracker, if connected): read the YAML of every file.
2. One table: task · title · `{pm_version}` · `{pm_status}` · each developer (nick, `{dev_status}`, `{round}`) · each QA (nick, `{qa_result}`, `{round}`) · `{depends_on}` · what waits for whom.
3. Flag conflicts: a file made against an old `{pm_version}`, an acceptance criterion done in one file and missing in another, a pass without evidence.
4. Add the recent commits and pull requests that name a task ID, one line each.
