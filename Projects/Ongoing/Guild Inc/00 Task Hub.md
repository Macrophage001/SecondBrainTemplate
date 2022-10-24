---
project: Guild Inc
tags: ['projects/guild-inc/tasks/hub']
type: 'tasks'
created: 2022-10-22 17:01
---

> [!important] Legend
> - #important For tasks that need to be completed ASAP.
> - #bug Problems in the codebase.
> - #bug/fixed Marks a bug as fixed.
> - #important/completed Marks a task as completed. 

---

## In Progress
---

```dataviewjs
const pages = dv.pages('"Projects/Ongoing/Guild Inc"');
dv.taskList(pages.file.tasks
			.where(t => !t.completed))
```


## Completed
---

```dataviewjs
const pages = dv.pages('"Projects/Ongoing/Guild Inc"');
dv.taskList(pages.file.tasks
			.where(t => t.completed))
```
