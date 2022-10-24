## An archive of all my Daily Notes

---

🚢 [[00 Ship's Log | Ship's Log]] | 📚[[00 Media Log | Media Log]] |  💡[[00 Discoveries Log | Discoveries]] | 🏋️‍♂️[[00 Workout Log | Workout Log]] | ❗[[00 Tasks Log | Tasks Log]]

## Last 7 Days

```dataviewjs
const generateTableData = (meta) => {
	return `<strong>${meta.title}</strong><br><br>${meta.Summary} <br>${meta.file.link}`
}

dv.table(['Entries'], dv.pages('"Diary/Daily Notes"')
		 .limit(7)
		 .sort(p => p.file.name, 'desc')
		 .map(n => [generateTableData(n)]))
```


## Search
> [!info] Parameters
> - @field: NotesInRange
> 	- @type: Range(YYYY-YYYY)
> 	- @description: Finds all notes within given range
> 	- @options: * - Wildcard symbol
> 	- @example: 
> 		- `*-2024` = All notes before 2024
> 		- `2020-*` = All notes after 2024

**NotesInRange**:: 2020-*

---
```dataviewjs

if (dv.current().NotesInRange !== null) {
	const yearRange = dv.current().NotesInRange.split('-');
	const generateTableData = (meta) => {
		return `<strong>${meta.title}</strong><br><br>${meta.Summary} <br>${meta.file.link}`
	}
	
	const yearRangePredGenerator = yearRange => file => {
		if (yearRange[0] === '*') {
			return file.day <= this.date(`${yearRange[1]}-01-01`)
		} else if (yearRange[1] === '*') {
			return file.day >= this.date(`${yearRange[0]}-01-01`)
		} else {
			return file.day >= this.date(`${yearRange[0]}-01-01`) && file.day <= this.date(`${yearRange[1]}-01-01`)
		}
	}
	
	if (yearRange) {
		const yearRangePred = yearRangePredGenerator(yearRange);
		dv.table(['Entries'], dv.pages('"Diary/Daily Notes"')
				 .where(n => yearRangePred(n.file))
				 .sort(p => p.file.name, 'desc')
				 .map(n => [generateTableData(n)]))
	}
}

```
