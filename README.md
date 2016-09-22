# ES2015 / ES NEXT Modules Syntax

> tl;dr

### Table of Contents

* [**:arrow_down: Basic Imports**](#arrow_down-basic-imports)
  * `Default`
  * `Named`
  * `Alias`
  * `Namespace`
  * `Bare`
* [**:arrow_double_down: Advanced Imports**](#arrow_double_down-advanced-imports)
  * `Default` with `Named` or `Namespace` (mixed)
* [**:arrow_up: Basic Exports**](#arrow_up-basic-exports)
  * `Default`
  * `Named`
  * `Lazy`
  * `Empty` (Unambiguous JavaScript Grammar)
* [**:arrow_double_up: Advanced Exports**](#arrow_double_up-advanced-exports)
  * Export with destructuring
  * Export with comma separated variables
* [**:repeat: Basic Re-Exports**](#repeat-basic-re-exports)
  * `Named`
  * `Alias`
  * `Namespace`
* [**:twisted_rightwards_arrows: Advanced Re-Exports**](#twisted_rightwards_arrows-advanced-re-exports)
  * `Named` as `Default`
  * `Default` as `Default`
  * `Default` as `Named`
  * `Namespace` as aliased `Namespace` (ES Next proposal)

## :arrow_down: Basic Imports

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

## :arrow_double_down: Advanced Imports

> `Default` with `Named` or `Namespace` (mixed)

```javascript
import React, {Component, PropTypes} from 'react';
import module, * as moduleAll from 'module';
```

**Note:** Default export should always be preceded.

**[⬆ Back to top](#table-of-contents)**

## :arrow_up: Basic Exports

> `Default`

```javascript
// export value as default
export default Math.PI;

// export arrow function expression as default
export default (x) => x * x * x;

// export variable as default
const a = 123;
export default a;

// export class declaration as default
export default class {
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

// export function declaration as default
export default function (x) {
  return x * x * x;
}
```

**Note:** Default Export should be one per module.

> `Named`

```javascript
// export variable
export const pi = Math.PI;

// export variable, which contains arrow function expression
export const str = () => `
bla
bla
bla
`;

// export let variable, but will be read-only
export let foo = 'bar';

// export function declaration
export function gcd(a, b) {
  if (!b) {
    return a;
  }

  return gcd(b, a % b);
}

// export class declaration
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
  pi, // export
  calcPlus as plus, // export as alias
  getRandomInt as default, // export as default (trailing comma is not necessary)
};
```

> `Empty` (Unambiguous JavaScript Grammar)

```javascript
export {};
```

* [Unambiguous JavaScript Grammar](https://github.com/bmeck/UnambiguousJavaScriptGrammar)

**[⬆ Back to top](#table-of-contents)**

## :arrow_double_up: Advanced Exports

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

## :repeat: Basic Re-Exports

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

## :twisted_rightwards_arrows: Advanced Re-Exports

> `Named` as `Default`

```javascript
export {prop as default} from 'module';
```

> `Default` as `Default`

```javascript
export {default} from 'default';
export default from 'default'; // ES Next proposal
```

* [ECMAScript Proposal: export default from](https://github.com/leebyron/ecmascript-export-default-from)

> `Default` as `Named`

```javascript
export {default as prop} from 'module';
export prop from 'module'; // ES Next proposal
```

* [ECMAScript Proposal: export default from](https://github.com/leebyron/ecmascript-export-default-from)

> `Namespace` as aliased `Namespace` (ES Next proposal)

```javascript
export * as ns from 'module';
```

* [ECMAScript Proposal: export ns from](https://github.com/leebyron/ecmascript-export-ns-from)

**[⬆ Back to top](#table-of-contents)**

## License

[MIT](http://preco.mit-license.org/)
