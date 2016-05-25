# ES2015 / ES NEXT Modules Syntax

> HAAAX!

## :arrow_down_small: Basic Imports

> Default

```javascript
import module from 'module';
```

> Named

```javascript
import {prop} from 'module';
```

> Alias

```javascript
import {prop as alias} from 'module';
```

> All

```javascript
import * as module from 'module';
```

> Bare

```javascript
import 'module';
```

## :arrow_double_down: Advanced Imports

> Default with Named or All

```javascript
import React, {Component, PropTypes} from 'react';
import module, * as moduleAll from 'module';
```

**Note:** Default export should always be preceded.

## :arrow_up_small: Basic Exports

> Default (one per module)

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
export function(x) {
  return x * x * x;
}
```

> Named

```javascript
// export variable
export const pi = Math.PI;

// export variable, which contains arrow function expression
export const str = () => `
bla
bla
bla
`;

// export let variable, but read-only
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

> Lazy

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
  getRandomInt as default // export as default
};
```

## :arrow_double_up: Advanced Exports

> Export with Destructuring

```javascript
const obj = {
  a: 123,
  b: 321
};

export const {a, b} = obj;
```

> Export with Comma Separated Variables

```javascript
export const a = 123, b = 321, c = 321;
```

## :repeat: Basic Re-Exports

> Named

```javascript
export {prop} from 'module';
```

> Alias

```javascript
export {prop as alias} from 'module';
```

> All Entries (except default export)

```javascript
export * from 'module';
```

## :twisted_rightwards_arrows: Advanced Re-Exports

> Named Export as Default

```javascript
export {prop as default} from 'module';
```

> Default Export as Default

```javascript
export {default} from 'default';
export default from 'default'; // ES NEXT proposal
```

* https://github.com/leebyron/ecmascript-export-default-from

> Default Export as Named

```javascript
export {default as prop} from 'module';
export prop from 'module'; // ES NEXT proposal
```

* https://github.com/leebyron/ecmascript-export-default-from

> All Entries as Namespace (ES NEXT proposal)

```javascript
export * as ns from 'module';
```

* https://github.com/leebyron/ecmascript-export-ns-from

## License

[MIT](http://preco.mit-license.org/)
