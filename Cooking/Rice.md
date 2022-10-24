---
title: ‘Alton Brown’s Rice Recipe’
src: ‘https://www.youtube.com/watch?v=9Qe-7tuMOIY’
original_cook: ‘Alton Brown’
cook_time: 1200
ingredients: [Rice, Water, Butter]
ingredient_units: [cup, cup, tbsp]
ingredient_ratios: [1, 1.5, 1]
default_servings: 2
default_serving_size: 0.75
serving_unit: 'cup'
---


## Ingredients
---
> [!info] Parameters
> - @field: Servings
> 	- @type: Int
> 	- @description: Used to calculate ingredient quantities.

### Servings:: 2
#### *Serving Size: 0.75 cup*
```dataviewjs
const ingredients = dv.current().ingredients;
const defaultServings = dv.current().default_servings;
const servings = parseInt(dv.current().Servings);
const ratios = dv.current().ingredient_ratios.map(r => r / defaultServings);
const units = dv.current().ingredient_units;

const calculateIngredientRatios = () => {
	return ratios.map(r => r * servings);
}

const newRatios = calculateIngredientRatios();
const newIngredientsList = newRatios.map((r, i) => {
	const unit = units[i];
	const ingredient = ingredients[i];

	return `${r} ${unit}${r > 1 ? 's' : ''} of ${ingredient}`
})

dv.list(newIngredientsList);
```
## Recipe:

1. Place rice and butter in pot on medium heat.
2. Saute rice until it starts release a nutty smell.
3. Place heavy lid / pot lid with tinfoil on top of pot and prepare to pour pre-boiled water.
4. Very carefully, pour pre-boiled water onto rice. ⚠

> [!warning] VERY HOT
> **There will be sputtering and a lot of steam, don’t stand too close and make sure to wear a mitt when pouring**

5. Reduce heat to low and let simmer for **20min**.

## References:
[Alton Brown’s Rice Video](https://www.youtube.com/watch?v=9Qe-7tuMOIY)
