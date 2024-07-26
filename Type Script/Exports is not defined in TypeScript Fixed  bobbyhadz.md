## [#](https://bobbyhadz.com/blog/typescript-uncaught-referenceerror-exports-is-not-defined#table-of-contents) Table of Contents

1.  [Browser - Reference Error: exports is not defined](https://bobbyhadz.com/blog/typescript-uncaught-referenceerror-exports-is-not-defined#browser---referenceerror-exports-is-not-defined)
2.  [Node.js - Reference Error: exports is not defined](https://bobbyhadz.com/blog/typescript-uncaught-referenceerror-exports-is-not-defined#nodejs---referenc eerror-exports-is-not-defined)

## [#](https://bobbyhadz.com/blog/typescript-uncaught-referenceerror-exports-is-not-defined#referenceerror-exports-is-not-defined-in-typescript) Reference Error: exports is not defined in TypeScript

**To solve the "Uncaught Reference Error: exports is not defined", add a script tag that defines an `exports` variable above your JS script tag if in the browser, or remove the `type` attribute if set to `module` in your `package.json` file in Node.js.**

## [#](https://bobbyhadz.com/blog/typescript-uncaught-referenceerror-exports-is-not-defined#browser---referenceerror-exports-is-not-defined) Browser - Reference Error: exports is not defined

If you got the error in the browser, try defining a global `exports` variable above the script tags that load your JS files.

```html
<script>var exports = {};</script> <!-- 👇️ your JS script should be below --> <script src="index.js"></script>
```

This defines the `exports` variable and sets it to an empty object, so you won't get an error if properties are accessed on it.

Browsers don't support the CommonJS syntax (unless you use a tool like Webpack) of `require` and `module.exports` which causes the error.

If you run your code in the browser, try removing the `module` property from your [tsconfig.json](https://bobbyhadz.com/blog/typescript-generate-tsconfig-json) file and set `target` to `es6`.

```json
{ "compilerOptions": { "target": "es6", // 👈️ set this to es6 // "module": "commonjs", // 👈️ REMOVE this (if browser env) } }
```

When you remove the [module](https://www.typescriptlang.org/tsconfig#module) option and set `target` to `es6`, your [ES6 modules](https://www.typescriptlang.org/docs/handbook/modules.html#handbook-content) imports and exports won't get compiled to the older CommonJS syntax that browsers don't support.

Modern browsers support all ES6 features so ES6 is a good choice.

## [#](https://bobbyhadz.com/blog/typescript-uncaught-referenceerror-exports-is-not-defined#set-type-to-module-on-your-script-tags) Set `type` to `module` on your `script` tags

If this doesn't work, try setting the `type` attribute to `module` on your `script` tags.

```html
<!-- 👇️ correct path according to your setup --> <script type="module" src="index.js"></script>
```

And import and export using the ES6 Modules syntax.

```javascript
import {v4} from 'uuid' export function sum(a, b) { return a + b; }
```

When you set `module` to `commonjs` in your `tsconfig.json`, you instruct TypeScript to emit CommonJS files and browsers don't support the CommonJS syntax, so this is a very likely cause of the error.

I've also written a detailed guide on [how to import values from another file in TS](https://bobbyhadz.com/blog/typescript-import-class-from-another-file).

## [#](https://bobbyhadz.com/blog/typescript-uncaught-referenceerror-exports-is-not-defined#nodejs---referenceerror-exports-is-not-defined) Node.js - Reference Error: exports is not defined

If you got the error in a Node.js application, try removing the `type` attribute from your `package.json` file if it's set to `module`.

```json
{ "type": "module", // 👈️ remove this }
```

When `type` is set to `module` we aren't able to use the `exports` and `require` syntax of CommonJS and we have to stick to ES Modules syntax for all of our imports and exports.

This happens when you have `type` set to `module` in your `package.json` file, but have `module` set to `commonjs` in your `tsconfig.json` file.

These two options aren't compatible because `type` = `module` instructs Node.js to use the ES Modules syntax and `module` = `commonjs` instructs TypeScript to emit CommonJS files.

Open your `tsconfig.json` file and make sure it looks something like the following.

```json

{ "compilerOptions": { "target": "es6", "module": "commonjs", "esModuleInterop": true, "moduleResolution": "node", // ... your other options } }
```

Your [target](https://www.typescriptlang.org/tsconfig#target) option should be at least `es6` and [module](https://www.typescriptlang.org/tsconfig#module) should be set to `commonjs`.

Make sure you use the [ES6 modules](https://www.typescriptlang.org/docs/handbook/modules.html#handbook-content) syntax for your imports and exports.

```typescript

import {myFunction} from './myFile' export function sum(a:number, b:number) { return a + b; }
```

Node.js supports the CommonJS syntax.

When you use the ES modules syntax and instruct TypeScript to emit CommonJS code by setting `module` to `commonjs`, the `export` in the example gets compiled to CommonJS and should work.

The only reason for it not to work is when you emit CommonJS files but have instructed Node.js to use the ES6 Module syntax to read them.

## [#](https://bobbyhadz.com/blog/typescript-uncaught-referenceerror-exports-is-not-defined#additional-resources) Additional Resources

You can learn more about the related topics by checking out the following tutorials:

-   [How to Import a JSON file in TypeScript](https://bobbyhadz.com/blog/typescript-import-json-file)
-   [Import 2 classes with same name in JavaScript or TypeScript](https://bobbyhadz.com/blog/typescript-import-two-classes-with-same-name)
-   [TypeScript: Cannot use import statement outside a module](https://bobbyhadz.com/blog/typescript-cannot-use-import-statement-outside-module)
-   [Module has no default export Error in TypeScript \[Solved\]](https://bobbyhadz.com/blog/typescript-module-has-no-default-export)
-   [Module has no exported member error in TypeScript \[Solved\]](https://bobbyhadz.com/blog/typescript-module-has-no-exported-member)
-   [Import and use the 'fs' module in TypeScript](https://bobbyhadz.com/blog/typescript-import-use-fs-module)