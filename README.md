# ES2015 / ES NEXT Modules Syntax

> HAAAX!

## :arrow_down_small: Basic Imports

### :beginner: Default

```javascript
import module from 'module';
```

### :beginner: Named

```javascript
import {prop} from 'module';
```

### :beginner: Alias

```javascript
import {prop as alias} from 'module';
```

### :beginner: All

```javascript
import * as module from 'module';
```

### :beginner: Bare

```javascript
import 'module';
```

## :arrow_double_down: Advanced Imports

### :beginner: Default with Named or All

```javascript
import React, {Component, PropTypes} from 'react';
import module, * as moduleAll from 'module';
```

**Note:** Default export should always be preceded.

## :arrow_up_small: Basic Exports

### :beginner: Default (one per module)

```javascript
// variable default export
export default Math.PI;

// arrow function default export
export default (x) => {
  if (!b) {
    return a;
  }

  return gcd(b, a % b);
}

// class default export
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
};

// variable default export
const a = 123;
export default a;
```

### :beginner: Named

```javascript
// const named export
export const pi = Math.PI;

// arrow function named export
export const str = () => `
bla
bla
bla
`;

// let named export
export let foo = 'bar';

// function named export
export function gcd(a, b) {
  if (!b) {
    return a;
  }

  return gcd(b, a % b);
}

// class named export
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
};
```

### :beginner: Lazy

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

### :beginner: Export with Destructuring

```javascript
const obj = {
  a: 123,
  b: 321
};

export const {a, b} = obj;
```

### :beginner: Export with Comma Separated Variables

```javascript
export const a = 123, b = 321, c = 321;
```

## :repeat: Basic Re-Exports

### :beginner: Named

```javascript
export {prop} from 'module';
```

### :beginner: Alias

``` javascript
export {prop as alias} from 'module';
```

### :beginner: All Entries (except default export)

```javascript
export * from 'module';
```

## :twisted_rightwards_arrows: Advanced Re-Exports

### :beginner: Named Export as Default

```javascript
export {prop as default} from 'module';
```

### :beginner: Default Export as Default

```javascript
export {default} from 'default';
export default from 'default'; // ES NEXT proposal
```

* https://github.com/leebyron/ecmascript-export-default-from

### :beginner: Default Export as Named

```javascript
export {default as prop} from 'module';
export prop from 'module'; // ES NEXT proposal
```

* https://github.com/leebyron/ecmascript-export-default-from

### :beginner: All Entries as Namespace (ES NEXT proposal)

```javascript
export * as ns from 'module';
```

* https://github.com/leebyron/ecmascript-export-ns-from

## License

[MIT](http://preco.mit-license.org/)
