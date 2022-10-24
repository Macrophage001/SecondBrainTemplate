#web-development/css/article/styling-axioms

## Lobotomized Owl Combinator

### Concerns

- Shaping the content around the style instead of the other way around.
- Creating bloat by styling named elements with similar values to others.

### Solution:


> “All elements in the flow of the document that proceed other elements must receive a top margin of one line.”
> ~ Heydon Pickering, [Axiomatic CSS and Lobotimized Owls](https://alistapart.com/article/axiomatic-css-and-lobotomized-owls/)

```css
* + *: {
	margin-top: 1.5em;
}
```

### Resources:
[Axiomatic CSS and Lobotomized Owls](https://alistapart.com/article/axiomatic-css-and-lobotomized-owls/#section8)
[Adjacent Sibling Combinator](https://developer.mozilla.org/en-US/docs/Web/CSS/Adjacent_sibling_combinator)
[Spacing The Bottom of Modules](https://css-tricks.com/spacing-the-bottom-of-modules/)
