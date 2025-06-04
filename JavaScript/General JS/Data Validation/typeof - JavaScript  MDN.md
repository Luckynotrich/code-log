Baseline

Widely available

The **`typeof`** operator returns a string indicating the type of the operand's value.

## [Try it](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof#try_it)

```js

console.log(typeof 42);
// Expected output: "number"

console.log(typeof "blubber");
// Expected output: "string"

console.log(typeof true);
// Expected output: "boolean"

console.log(typeof undeclaredVariable);
// Expected output: "undefined"
```

## [Syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof#syntax)

### [Parameters](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof#parameters)

[`operand`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof#operand)

An expression representing the object or [primitive](https://developer.mozilla.org/en-US/docs/Glossary/Primitive) whose type is to be returned.

## [Description](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof#description)

The following table summarizes the possible return values of `typeof`. For more information about types and primitives, see also the [JavaScript data structure](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Data_structures) page.

| Type | Result |
| --- | --- |
| [Undefined](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/undefined) | `"undefined"` |
| [Null](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/null) | `"object"` ([reason](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof#typeof_null)) |
| [Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean) | `"boolean"` |
| [Number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number) | `"number"` |
| [BigInt](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/BigInt) | `"bigint"` |
| [String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) | `"string"` |
| [Symbol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol) | `"symbol"` |
| [Function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function) (implements \[\[Call\]\] in ECMA-262 terms; [classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/class) are functions as well) | `"function"` |
| Any other object | `"object"` |

This list of values is exhaustive. No spec-compliant engines are reported to produce (or had historically produced) values other than those listed.

## [Examples](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof#examples)

### [Basic usage](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof#basic_usage)

```js

// Numbers
typeof 37 === "number";
typeof 3.14 === "number";
typeof 42 === "number";
typeof Math.LN2 === "number";
typeof Infinity === "number";
typeof NaN === "number"; // Despite being "Not-A-Number"
typeof Number("1") === "number"; // Number tries to parse things into numbers
typeof Number("shoe") === "number"; // including values that cannot be type coerced to a number

typeof 42n === "bigint";

// Strings
typeof "" === "string";
typeof "bla" === "string";
typeof `template literal` === "string";
typeof "1" === "string"; // note that a number within a string is still typeof string
typeof typeof 1 === "string"; // typeof always returns a string
typeof String(1) === "string"; // String converts anything into a string, safer than toString

// Booleans
typeof true === "boolean";
typeof false === "boolean";
typeof Boolean(1) === "boolean"; // Boolean() will convert values based on if they're truthy or falsy
typeof !!1 === "boolean"; // two calls of the ! (logical NOT) operator are equivalent to Boolean()

// Symbols
typeof Symbol() === "symbol";
typeof Symbol("foo") === "symbol";
typeof Symbol.iterator === "symbol";

// Undefined
typeof undefined === "undefined";
typeof declaredButUndefinedVariable === "undefined";
typeof undeclaredVariable === "undefined";

// Objects
typeof { a: 1 } === "object";

// use Array.isArray or Object.prototype.toString.call
// to differentiate regular objects from arrays
typeof [1, 2, 4] === "object";

typeof new Date() === "object";
typeof /regex/ === "object";

// The following are confusing, dangerous, and wasteful. Avoid them.
typeof new Boolean(true) === "object";
typeof new Number(1) === "object";
typeof new String("abc") === "object";

// Functions
typeof function () {} === "function";
typeof class C {} === "function";
typeof Math.sin === "function";
```

### [typeof null](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof#typeof_null)

```js

// This stands since the beginning of JavaScript
typeof null === "object";
```

In the first implementation of JavaScript, JavaScript values were represented as a type tag and a value. The type tag for objects was `0`. `null` was represented as the NULL pointer (`0x00` in most platforms). Consequently, `null` had `0` as type tag, hence the `typeof` return value `"object"`. ([reference](https://2ality.com/2013/10/typeof-null.html))

A fix was proposed for ECMAScript (via an opt-in), but [was rejected](https://web.archive.org/web/20160331031419/http://wiki.ecmascript.org:80/doku.php?id=harmony:typeof_null). It would have resulted in `typeof null === "null"`.

### [Using new operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof#using_new_operator)

All constructor functions called with [`new`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/new) will return non-primitives (`"object"` or `"function"`). Most return objects, with the notable exception being [`Function`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function), which returns a function.

```
const str = new String("String");
const num = new Number(100);

typeof str; // "object"
typeof num; // "object"

const func = new Function();

typeof func; // "function"
```

### [Need for parentheses in syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof#need_for_parentheses_in_syntax)

The `typeof` operator has higher [precedence](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_precedence) than binary operators like addition (`+`). Therefore, parentheses are needed to evaluate the type of an addition result.

```js

// Parentheses can be used for determining the data type of expressions.
const someData = 99;

typeof someData + " foo"; // "number foo"
typeof (someData + " foo"); // "string"
```

### [Interaction with undeclared and uninitialized variables](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof#interaction_with_undeclared_and_uninitialized_variables)

`typeof` is generally always guaranteed to return a string for any operand it is supplied with. Even with undeclared identifiers, `typeof` will return `"undefined"` instead of throwing an error.

```js

typeof undeclaredVariable; // "undefined"
```

However, using `typeof` on lexical declarations ([`let`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let) [`const`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const), and [`class`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/class)) in the same block before the place of declaration will throw a [`ReferenceError`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ReferenceError). Block scoped variables are in a _[temporal dead zone](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let#temporal_dead_zone_tdz)_ from the start of the block until the initialization is processed, during which it will throw an error if accessed.

```js

typeof newLetVariable; // ReferenceError
typeof newConstVariable; // ReferenceError
typeof newClass; // ReferenceError

let newLetVariable;
const newConstVariable = "hello";
class newClass {}
```

### [Exceptional behavior of document.all](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof#exceptional_behavior_of_document.all)

All current browsers expose a non-standard host object [`document.all`](https://developer.mozilla.org/en-US/docs/Web/API/Document/all) with type `undefined`.

```js

typeof document.all === "undefined";
```

Although `document.all` is also [falsy](https://developer.mozilla.org/en-US/docs/Glossary/Falsy) and [loosely equal](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Equality) to `undefined`, it is not [`undefined`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/undefined). The case of `document.all` having type `"undefined"` is classified in the web standards as a "willful violation" of the original ECMAScript standard for web compatibility.

### [Custom method that gets a more specific type](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof#custom_method_that_gets_a_more_specific_type)

`typeof` is very useful, but it's not as versatile as might be required. For example, `typeof []` is `"object"`, as well as `typeof new Date()`, `typeof /abc/`, etc.

For greater specificity in checking types, here we present a custom `type(value)` function, which mostly mimics the behavior of `typeof`, but for non-primitives (i.e., objects and functions), it returns a more granular type name where possible.

```js

function type(value) {
  if (value === null) {
    return "null";
  }
  const baseType = typeof value;
  // Primitive types
  if (!["object", "function"].includes(baseType)) {
    return baseType;
  }

  // Symbol.toStringTag often specifies the "display name" of the
  // object's class. It's used in Object.prototype.toString().
  const tag = value[Symbol.toStringTag];
  if (typeof tag === "string") {
    return tag;
  }

  // If it's a function whose source code starts with the "class" keyword
  if (
    baseType === "function" &&
    Function.prototype.toString.call(value).startsWith("class")
  ) {
    return "class";
  }

  // The name of the constructor; for example `Array`, `GeneratorFunction`,
  // `Number`, `String`, `Boolean` or `MyCustomClass`
  const className = value.constructor.name;
  if (typeof className === "string" && className !== "") {
    return className;
  }

  // At this point there's no robust way to get the type of value,
  // so we use the base implementation.
  return baseType;
}
```

For checking potentially non-existent variables that would otherwise throw a [`ReferenceError`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ReferenceError), use `typeof nonExistentVar === "undefined"` because this behavior cannot be mimicked with custom code.

## [Specifications](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof#specifications)

| Specification                                                                                                                                                    |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [ECMAScript® 2026 Language Specification  <br># sec-typeof-operator](https://tc39.es/ecma262/multipage/ecmascript-language-expressions.html#sec-typeof-operator) |

## [Browser compatibility](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof#browser_compatibility)

## [See also](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof#see_also)