
```dataviewjs
const pages = dv.pages('#functional-programming')
const dView = pages.map(p => [p.file.link, p.tags[0], p.description])

dv.header(2, "Analysis")
dv.table(['Title', 'Tag', 'Description'], dView)
```

