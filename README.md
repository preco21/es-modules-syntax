# ES2015 / ES NEXT Modules Syntax

> HAAAX!

## Basic Imports

### Default

```javascript
import module from 'module';
```

### Named

```javascript
import {prop} from 'module';
```

### Alias

```javascript
import {prop as alias} from 'module';
```

### All

```javascript
import * as module from 'module';
```

### Bare

```javascript
import 'module';
```

## Advanced Imports

### Default with Named and All

```javascript
import React, {Component, PropTypes} from 'react';
import module, * as moduleAll from 'module';
```

**Note:** Default export always should precede.

## Basic Exports

### Default (one per module)

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

// class deafult export
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
```

### Named

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

### Lazy

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

## Advanced Exports

### Export with Destructuring

```javascript
const obj = {
  a: 123,
  b: 321
};

export const {a, b} = obj;
```

### Export with Comma Separated Variables

```javascript
export const a = 123, b = 321, c = 321;
```

## Basic Re-Exports

### Named

```javascript
export {prop} from 'module';
```

### Alias

``` javascript
export {prop as alias} from 'module';
```

### All Entries (except default export)

```javascript
export * from 'module';
```

## Advanced Re-Exports

### Named Export as Default

```javascript
export {prop as default} from 'module';
```

### Default Export as Default

```javascript
export {default} from 'default';
export default from 'default'; // ES NEXT proposal
```

* https://github.com/leebyron/ecmascript-export-default-from

### Default Export as Named

```javascript
export {default as prop} from 'module';
export prop from 'module'; // ES NEXT proposal
```

* https://github.com/leebyron/ecmascript-export-default-from

### All Entries as Namespace (ES NEXT proposal)

```javascript
export * as ns from 'module';
```

* https://github.com/leebyron/ecmascript-export-ns-from

## License

[MIT](http://preco.mit-license.org/)
