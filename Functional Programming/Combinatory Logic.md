---
tags: ['functional-programming/combinatory-logic']
type: 'analysis'
description: 'Combinatory Logic: a model of computation equivalent to [[Lamda Calculus]], but without abstraction.'
---

### Combinatory Logic: a model of computation equivalent to [[Lamda Calculus]], but without abstraction.

## Combinators
---

*A combinator is a function with no free variables, or no variables that exist within the function that were not passed in to the function*

- **Identity**:
```js
I = a => a
```
Example:

```dataviewjs
const I = a => a;

dv.el('p', `The result of I(1) = ${I(1)}`)
dv.el('p', `The result of I(2) = ${I(2)}`)
dv.el('p', `The result of I('Hello World') = ${I('Hello World')}`)
```
---

- **Mockingbird**: *Takes a function and calls it on itself.*
- A simple form of recursion.
```js
M = f => f(f);
```
Example:
```dataviewjs
const M = f => f(f);

dv.el('p', `The result of M(() => 'Hello World') = ${M(() => 'Hello World')}`)
dv.el('p', `The result of M(x => x + 1) = ${M((x) => x + 1)}`)
```

---

- **Kestrel**: *Takes two arguments, and returns the first*
- Useful when needing constant values.
- Useful in boolean logic as true.
```js
K = a => b => a;

// Example:
K5 = K(5);
K5(2) // = 5
K5("Hello") // = 5
```
---

- **Kite**: *Takes two arguments, returns the second*
- Combination: Kestrel + Identity
- Useful in boolean logic as false.
```js
KI = a => b => b;
KI = K(I);
```
---

- **Cardinal**: *Applies the first function to the second argument, passing the third argument to the resulting function from the first application*
- Can also be used boolean logic as the **NOT** operator.
- Yields exact same result as **Kite Combinator**
```js
C = f => a => b => f(b)(a);
NOT = C
```
- **AND**: Takes two boolean functions and will return the composition of both inputs if true, otherwise will return the first boolean function.
```js
AND = p => q => p(q)(KI)
AND = p => q => p(q)(p)
```
- **Starling**
```js
S = a => b => c => a(c)(b(c))
```
- **Iota**
- Can be used to build **any other combinatory function**
```js
i = f => ((f(S))(K))

I = i(i)
K = (i(i(i(i))))
S = (i(i(i(i(i)))))
```
- **Bluebird (Compose)**
```js
B = f => g => a => f(g(a))
```
- **Blackbird (Binary Compose)**
```js
B1 = f => g => a => b => f(g(a)(b))

B1 = B(B(B))
```
- **Y Combinator**
```js
Y = f =>(g => x => f(g(g))(x))
		(g => x => f(g(g))(x))
		
Y = f => M(m => a => f(m(m))(a))

// Javascript friendly
why = fn => 
	(maker => (...args) => fn(maker(maker), ...args))
	(maker => (...args) => fn(maker(maker), ...args))
```
## Church Numerals
---

- Zero
```js
n0 = f => a => a
```
- Once
```js
n1 = f => a => f(a)
```
- Twice
```js
n2 = f => a => f(f(a))
```
- Thrice
```js
n3 = f => a => f(f(f(a)))
```
- **Successor (Succ)**: *Applies an additional operation 'f' to 'n'*
- Can also be created using the Bluebird.
```js
succ = n => f => a => f(n(f(a)))
succ = n => f => B(f)(n(f))
```
- **Add**: *Adds two operations together*
```js
add = n => k => n(succ)(k)
```
- **Mult**:
```js
mult = B
```
- Is0:
- Used to check if a value is zero.
- If at least one function application is attempted, then this function will always return `KI` or `False`, Otherwise it will return `K` or `True`.
```js
Is0 = n => n(K(KI))(K)

Is0(n0)

n0 => n0(K(KI))(K);

n0 = f => a => a;

n0((a => b => a)(KI))(K);

 = (a => b => a)(KI)
 = (KI => b => KI)(K)
 = K

// The function `KI => b => KI` is being ignored as n0 does 0 applications of the function.
n0((KI => b => KI))(K);

(KI => b => KI)(K);
KI(K)
```
- **Pred**:
```js
pred = n => fst(n(phi)(V(n0)(n0)))
```
- **Vireo (AKA Pair)**: *Data structure for holding two arguments*
```js
V = a => b => f => f(a)(b)
```
- **Phi**:
```js
phi = p => V(snd(p))(succ(snd(p)))
```
- **Subtract**:
```js
sub = n => k => k(pred)(n)

sub(n2)(n1)

// Example Subtract

// beta-reduction
= n1(pred)(n2)
= n1(n => fst(n(phi)(V(n0)(n0))))(n2)
= n1(fst(n2(phi)(V(n0)(n0))))
= n1(fst([n0, n1])) // First Application
= n1(fst([n1, n2])) // Second Application
= n1(n1) // First of pair = n1
= n1
```

## Resources:
---
- ### [A Flock of Functions: Lambda Calculus and Combinatory Logic in JavaScript | Gabriel Lebec @ DevTalks](https://www.youtube.com/watch?v=6BnVo7EHO_8&t=1038s)
- ### [A Flock of Functions: Combinators, Lambda Calculus, & Church Encodings in JS - Part II](https://www.youtube.com/watch?v=pAnLQ9jwN-E)
- ### [Essentials: Functional Programming's Y Combinator - Computerphile](https://www.youtube.com/watch?v=9T8A89jgeTI&t=623s)
- ### [Combinatory Logic](https://en.wikipedia.org/wiki/Combinatory_logic#mw-content-text)