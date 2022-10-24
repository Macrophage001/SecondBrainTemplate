---
tags: ['functional-programming/y-combinator']
type: 'analysis'
description: 'Provides a means of recursion when language does not support it.'
---

### Definition: Provides a means of recursion when language does not support it.

```js
Y = f => (g => x => f(g(g))(x))
		 (g => x => f(g(g))(x))
```