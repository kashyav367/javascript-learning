1. Rest parameters (...rest)
- Rest parameter collects remaining arguments passed to a function into a real array.
- There can be only one rest parameter, and it must be the last parameter.

Example
```js
function sum(...numbers) {
  return numbers.reduce((a, b) => a + b, 0);
}

sum(1, 2, 3, 4); // numbers = [1, 2, 3, 4]
```
Or with named parameters:

```js
function show(a, b, ...rest) {
  console.log(a);    // 1
  console.log(b);    // 2
  console.log(rest); // [3, 4, 5]
}

show(1, 2, 3, 4, 5);
```
2. Spread syntax (...spread)
- Spread expands an iterable (array, string, set, etc.) or object into individual elements.

Example
```js
let nums = [1, 2, 3];

Math.max(...nums); // same as Math.max(1, 2, 3)
```

3. Spread vs Object.assign
- Spread syntax can be used in place of Object.assign

```js
let obj1 = { a: 1, b: 2 };
let obj2 = { c: 3 };

let merged = { ...obj1, ...obj2 };
// { a: 1, b: 2, c: 3 }

//Equivalent to:
Object.assign({}, obj1, obj2);
```

Key notes:
- Spread creates a shallow copy
- Later properties overwrite earlier ones

```js
{ ...{a: 1}, ...{a: 2} } // { a: 2 }
```