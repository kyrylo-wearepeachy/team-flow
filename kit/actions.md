# team-flow actions (any role)

Common actions any role can ask for. Each one: work out by yourself which of your tools fit (browser, design access, code access, connectors), say in one line what you will use and what you propose, and act after the go-ahead. If a tool is missing, say what you would need and offer the simplest way around it (e.g. screenshots from the user). Never set up a tool yourself.

## Task draft

A quick task file from anything: one sentence, a link, a screenshot.

1. Read what the user gave. If it is a link to a task tracker task and the tracker is connected, read the task, its comments and attachments.
2. Fill the PM template as far as the facts go: header, one or more "Done when" items, Materials with a one-line description each. Unknown → `—`; open points go to Questions.
3. Take the next ID with the project's `task_prefix`.
4. Show, write after the go-ahead, report. The PM file stays the task's passport; a non-PM author is named in "By".

## Find the cause

The likely cause of a problem, before anyone fixes it.

1. Look at every source you can reach: the page (in a browser, at the width where it breaks), the design if one is linked, the screenshots, the site code.
2. Narrow it down: the element, its styles or script, the line that makes it behave so.
3. Answer in 3-5 lines: "Most likely: <cause>, `file:line`, because <what you saw>." Add what else it could be, and how sure you are.
4. Read-only. If a task exists, offer to put it into the PM file's "Suggested approach" or into your own file's Notes.

## Visual check

Compare the site with the design, for the pages in the task's "Change scope".

1. Find the design: a link in the PM file (e.g. Figma) or design files the user gave. If you can read the design (a connector or design tool you have), take the frames for the same pages and widths. If not, ask the user for screenshots of the frames.
2. Open each page at the frame's width (see "Responsive view").
3. Compare what matters for the task: layout, spacing, sizes, colours, texts. Ignore what is out of scope.
4. Write each difference as one line with the width and a screenshot pair (site · design). In a QA file they go to "Agent reading" as evidence, or to "Bugs".

## Responsive view

One page at several widths side by side, in one browser window, all at the same height.

- Default widths: 390 · 768 · 1024 · 1440. Wider frames are scaled down so all fit in one window.
- The ready page is the `responsive` template ([templates/responsive.html](templates/responsive.html)). Open it with the page URL: `responsive.html?url=<page URL>` (optional `&w=390,768,1024,1440`; the frames fill the window height, or set `&h=<px>`).
- Write the page only to the system temp folder, never into the project; it is the one file you may write outside the project folder.
- **First check what you can open.** Many sites forbid being shown in a frame (an `X-Frame-Options` header, or `frame-ancestors` in `Content-Security-Policy`), and then the frames stay empty. Check the page's headers, or try once.
- **If frames do not work, choose the way yourself** from what your environment allows, and tell the user in one line what you propose and why. For example: set each width in your browser in turn and show the screenshots side by side; use a tool you already have for this; or something else that fits. Never install anything for it; if the best way needs something new, describe it and let the user decide.
- Look for: overflow and sideways scroll, wrapped or cut text, overlapping elements, hidden or misplaced buttons, image cropping.
