↑ [[00 Daily Notes Hub | Daily Notes Hub]] 

---

📚[[00 Media Log | Media Log]] |  💡[[00 Discoveries Log | Discoveries]] | 🏋️‍♂️[[00 Workout Log | Workout Log]] | ❗[[00 Tasks Log | Tasks Log]]


## Happenings


```dataviewjs
dv.table(['File', 'Log'], dv.pages('"Diary/Daily Notes"')
		 .sort((a, b) => a - b)
		 .map(n => [n.file.name, n.LifeEvent]))
```

## Projects


```dataviewjs
dv.table(['File', 'Log'], dv.pages('"Diary/Daily Notes"')
		 .sort((a, b) => a - b)
		 .map(n => [n.file.name, n.Project]))
```