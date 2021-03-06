# ES2015 / ES NEXT modules syntax

> tl;dr

### Table of contents

* [**:arrow_down: Basic imports**](#arrow_down-basic-imports)
  * `Default`
  * `Named`
  * `Alias`
  * `Namespace`
  * `Bare`
* [**:arrow_double_down: Advanced imports**](#arrow_double_down-advanced-imports)
  * `Default` with `Named` or `Namespace` (mixed)
* [**:arrow_up: Basic exports**](#arrow_up-basic-exports)
  * `Default`
  * `Named`
  * `Lazy`
  * `Empty` (Unambiguous JavaScript Grammar)
* [**:arrow_double_up: Advanced exports**](#arrow_double_up-advanced-exports)
  * Export with destructuring
  * Export with comma separated variables
* [**:repeat: Basic re-exports**](#repeat-basic-re-exports)
  * `Named`
  * `Alias`
  * `Namespace`
* [**:twisted_rightwards_arrows: Advanced re-exports**](#twisted_rightwards_arrows-advanced-re-exports)
  * `Named` as `Default`
  * `Default` as `Named`
  * `Default` as `Default`
  * `Namespace` as aliased `Namespace` (ES Next proposal)

## :arrow_down: Basic imports

> `Default`

```javascript
import module from 'module';
```

> `Named`

```javascript
import {prop} from 'module';
```

> `Alias`

```javascript
import {prop as alias} from 'module';
```

> `Namespace`

```javascript
import * as moduleAll from 'module';
```

> `Bare`

```javascript
import 'module';
```

**[⬆ Back to top](#table-of-contents)**

## :arrow_double_down: Advanced imports

> `Default` with `Named` or `Namespace` (mixed)

```javascript
import React, {Component, PropTypes} from 'react';
import module, * as moduleAll from 'module';
```

**Note:** Default export should always be preceded.

**[⬆ Back to top](#table-of-contents)**

## :arrow_up: Basic exports

> `Default`

```javascript
/* Export value as default */
export default Math.PI;

/* Export arrow function expression as default */
export default (x) => x * x * x;

/* Export variable as default */
const a = 123;
export default a;

/* Export class declaration as default */
export default class A {
  constructor(a = 0) {
    this.setA(a);
  }

  getA() {
    return this.a;
  }

  setA(a = 0) {
    this.a = a;
  }
}

/* Export function declaration as default */
// In this case, you can omit the name of the function. Even if there is no function name it still treats to function declaration. This rule affects `classes` and `generator functions` as well.
// See http://exploringjs.com/es6/ch_modules.html#_default-export-style-1-labeling-declarations
export default function (x) {
  return x * x * x;
}
```

**Note:** Default Export should be one per module.

> `Named`

```javascript
/* Export variable */
export const pi = Math.PI;

/* Export variable, which contains arrow function expression */
export const str = () => `
bla
bla
bla
`;

/* Export let variable, but will be read-only */
export let foo = 'bar';

/* Export function declaration */
export function gcd(a, b) {
  if (!b) {
    return a;
  }

  return gcd(b, a % b);
}

/* Export class declaration */
export class A {
  constructor(a = 0) {
    this.setA(a);
  }

  getA() {
    return this.a;
  }

  setA(a = 0) {
    this.a = a;
  }
}
```

> `Lazy`

```javascript
const pi = Math.PI;

function calcPlus(a, b) {
  return a + b;
}

function getRandomInt(max = 10, min = 0) {
  return Math.trunc(min + Math.random() * (max - min + 1));
}

export {
  pi, // Export
  calcPlus as plus, // Export as alias
  getRandomInt as default, // Export as default (trailing comma is not necessary)
};
```

> `Empty` (Unambiguous JavaScript Grammar)

```javascript
export {};
```

* [Unambiguous JavaScript Grammar](https://github.com/bmeck/UnambiguousJavaScriptGrammar)

**[⬆ Back to top](#table-of-contents)**

## :arrow_double_up: Advanced exports

> Export with destructuring

```javascript
const obj = {
  a: 123,
  b: 321,
};

export const {a, b} = obj;
```

> Export with comma separated variables

```javascript
export const a = 123, b = 321, c = 321;
```

**[⬆ Back to top](#table-of-contents)**

## :repeat: Basic re-exports

> `Named`

```javascript
export {prop} from 'module';
```

> `Alias`

```javascript
export {prop as alias} from 'module';
```

> `Namespace`

```javascript
export * from 'module';
```

**Note:** _Namespace Entries Re-Export_ does not export `default`.

**[⬆ Back to top](#table-of-contents)**

## :twisted_rightwards_arrows: Advanced re-exports

> `Named` as `Default`

```javascript
export {prop as default} from 'module';
```

> `Default` as `Named`

```javascript
export {default as prop} from 'module';
export prop from 'module'; // ES Next proposal
```

* [ECMAScript Proposal: export default from](https://github.com/leebyron/ecmascript-export-default-from)

> `Default` as `Default`

```javascript
export {default} from 'module';
export default from 'module'; // ES Next proposal
```

* [ECMAScript Proposal: export default from](https://github.com/leebyron/ecmascript-export-default-from)

> `Namespace` as aliased `Namespace` (ES Next proposal)

```javascript
export * as ns from 'module';
```

* [ECMAScript Proposal: export ns from](https://github.com/leebyron/ecmascript-export-ns-from)

**[⬆ Back to top](#table-of-contents)**

## References

* [ECMAScript-262 6.0 specification](https://www.ecma-international.org/ecma-262/6.0/#sec-modules)
* [ExploringJS modules](http://exploringjs.com/es6/ch_modules.html)
* [MDN `import`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import)
* [MDN `export`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export)

## License

[MIT](http://preco.mit-license.org/)
