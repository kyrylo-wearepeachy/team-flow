---
# Source of the project variables (variables.md). Fill once; task files copy from here.
project: "{project}"
task_prefix: "{task_prefix}"
repository: "{repository}"
site: "{site}"
preview: "{preview}"
admin: "{admin}"
task_storage: "{task_storage}"
---

# Project: {project}

Role here: {role} · Me: {nick}

## Access

Only for this computer: where things are and how your agent reaches them.

| What | Access |
| --- | --- |
| site code | {code} · or code host connector · or no access |
| site / preview | browser · or no access |
| design | connector · or screenshots from the user |
| task storage | connector read · read and write · or files by hand |

## History

Your own record, one entry per task file you write, newest last. Never edit old entries.

### {now} · {task_id} · {role} · round {round} · PM v{pm_version}
Task:    {title}
Done:    what you did, in one or two lines
Content: what it came from: client message (date, a few words), files, design links
Links:   commit, tracker task, related tasks ("continues {task_id}")
