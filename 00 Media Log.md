↑ [[00 Daily Notes Hub | Daily Notes Hub]] 

---

💡[[00 Discoveries Log | Discoveries]] | 🚢 [[00 Ship's Log | Ship's Log]] | 🏋️‍♂️[[00 Workout Log | Workout Log]] | ❗[[00 Tasks Log | Tasks Log]]

Concatenated view of all the media I watch and a small review of each.

```dataviewjs
dv.header(2, 'Reading')
dv.table(['File', 'Log'], dv.pages('"Diary/Daily Notes"')
		 .sort((a, b) => a - b)
		 .map(n => [n.file.name, n.Reading]))
```

```dataviewjs
dv.header(2, 'Listening')
dv.table(['File', 'Log'], dv.pages('"Diary/Daily Notes"')
		 .sort((a, b) => a - b)
		 .map(n => [n.file.name, n.Listening]))
```


```dataviewjs
dv.header(2, 'Videos')
dv.table(['File', 'Log'], dv.pages('"Diary/Daily Notes"')
		 .sort((a, b) => a - b)
		 .map(n => [n.file.name, n.Video]))
```