↑ [[00 Daily Notes Hub | Daily Notes Hub]] 

---

🚢 [[00 Ship's Log | Ship's Log]] | 📚[[00 Media Log | Media Log]]  | 🏋️‍♂️[[00 Workout Log | Workout Log]] | ❗[[00 Tasks Log | Tasks Log]]


```dataviewjs
dv.header(2, 'Discoveries')
dv.table(['File', 'Log'], dv.pages('"Diary/Daily Notes"')
		 .sort((a, b) => a - b)
		 .map(n => [n.file.name, n.Discovery]))
```
