↑ [[00 Daily Notes Hub | Daily Notes Hub]] 

---

🚢 [[00 Ship's Log | Ship's Log]] |📚[[00 Media Log | Media Log]] |  💡[[00 Discoveries Log | Discoveries]] | 🏋️‍♂️[[00 Workout Log | Workout Log]]

## Tasks

```dataviewjs
const pages = dv.pages('"Diary/Daily Notes"').sort(p => p.file.name, 'desc');

dv.taskList(pages.file.tasks.where(t => !t.completed))
```
