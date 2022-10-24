---
Title:
created: <% tp.file.creation_date('YYYY-DD-MM') %>
---

↑ [[00 Daily Notes Hub | Daily Notes Hub]]

### [[<% tp.date.now('YYYY-MM-DD', -1) %>]]  ← | → [[<% tp.date.now('YYYY-MM-DD', 1) %>]]
---

- Summary::

## Discoveries
---
> [!important] Legend
> -   💡 = General discovery.
> -   📕 = Fiction Book.
> -   📘 = Nonfiction Book.
> -   📓 = Obsidian Related
> -   🛠 = Tool or Resource
> -   🎵 = New Music
> -   🏋️‍♂️ = Fitness Related
> -   🎨 = Art Related

- Discovery::

## 🚢 Ship's Log

### Tasks
---
> [!important] Legend
> - #remind-me 
> - #remind-me/project 
> - #remind-me/reading 
#### Unfinished:
---
```dataviewjs
const pages = dv.pages('"Diary/Daily Notes"')
const index = pages.indexOf(dv.current());
const prevPage = pages[index - 1];

dv.taskList(prevPage.file.tasks.where(t => {
	return t.text.includes('#remind-me') && !t.completed;
}))
```


- [ ] #remind-me/project ⏳ 

### Happenings
---

- LifeEvent:: 🧬 

### Projects
---
> [!important] Legend
> -   💡 = Ideas.
> -   ✍ = WIP Projects.
> -   🛠 = Polishing and Refinment.
> -   ✅ = Completed project milestone.
> -   ❗ = Serious error/bug that needs attention.

- Project:: ✍ 

### Reading
---
> [!important] Legend
> - ✅ = Finished Book.
> - 📖 = Currently Reading.
> - ✍ = Need to take notes.

- Reading:: 📚 

### Video
---
> [!important] Legend
> - ✅ = Finished Video
> - ✍ = Need to take notes.

- Video:: 📺 

### Workout
---

- Workout:: 🏋️‍♂️ 