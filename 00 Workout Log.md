↑ [[00 Daily Notes Hub | Daily Notes Hub]] 

---

🚢 [[00 Ship's Log | Ship's Log]] | 📚 [[00 Media Log | Media Log]] | 💡[[00 Discoveries Log | Discoveries]] | ❗[[00 Tasks Log | Tasks Log]]


## Workouts


```dataviewjs
dv.table(['File', 'Log'], dv.pages('"Diary/Daily Notes"')
		 .sort((a, b) => a - b)
		 .map(n => [n.file.name, n.Workout]))
```
