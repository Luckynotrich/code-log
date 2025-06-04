**To pass a comparison operator as a parameter** in JavaScript, one can pass a function that performs the comparison. This approach leverages the fact that functions are first-class citizens in JavaScript and can be passed as arguments to other functions.

```js
function compare(a, b, comparator) {
  return comparator(a, b);
}

function greaterThan(a, b) {
  return a > b;
}

function lessThan(a, b) {
  return a < b;
}

function equalTo(a, b) {
  return a === b;
}

let x = 10;
let y = 20;

console.log(compare(x, y, greaterThan)); // Output: false
console.log(compare(x, y, lessThan));    // Output: true
console.log(compare(x, x, equalTo));    // Output: true
```

In this example, the `compare` function takes two values (`a` and `b`) and a `comparator` function as arguments. The `comparator` function is then used to perform the actual comparison between `a` and `b`. Different comparison functions (`greaterThan`, `lessThan`, `equalTo`) can be passed to `compare` to achieve different comparison results.

Alternatively, arrow functions can be used for a more concise syntax:
```js
const compare = (a, b, comparator) => comparator(a, b);
const greaterThan = (a, b) => a > b;
const lessThan = (a, b) => a < b;
const equalTo = (a, b) => a === b;

let x = 10;
let y = 20;

console.log(compare(x, y, greaterThan));
console.log(compare(x, y, lessThan));
console.log(compare(x, x, equalTo));
```

This approach provides a flexible way to parameterize comparison logic in JavaScript functions.