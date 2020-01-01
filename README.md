![](assets/logo.png)

ReIterator is a node.js module which helps you avoid errors while accessing json from the big bad internet (and your own apis)

![](https://img.shields.io/travis/sudhanshuraheja/reiterator.svg)
![](https://img.shields.io/codecov/c/github/sudhanshuraheja/reiterator/master.svg)
![](https://img.shields.io/github/license/sudhanshuraheja/reiterator.svg)

## About

I created this package to simplify iterating across arrays and objects without hitting into errors. The Iterator is chainable, making it possible to access items as `i.$('first').$(0).$('second).value()`

## Quick Start

```bash
yarn add reiterator
```

```js
const Iterator = require("reiterator");
const i = new Iterator({ key: "abc" });
const value = i.$("key").value();
console.log(value);
```

The response should be `abc`

## The complete API

### Iterator functions

The package supports the following functions on the iterator

```js
const obj = { abc: [1, 2, 3, 4, 5], def: { ghi: "jkl", mno: 10 } };
i = new Iterator(obj);
i.$("abc").keys(); // [1,2,3,4,5]
i.$("def").keys(); // ['ghi', 'mno']
i.$("def")
  .$("ghi")
  .string(); // 'jkl'
i.$("def")
  .$("mno")
  .string(); // '10
i.$("def")
  .$("mno")
  .value(); // 10
```

What makes it easy is that

- `keys()` always returns an array or []
- `string()` always returns a string or ''

### Object functions

The package support the following functions on objects

```js
const array = Iterator.isArray([123]);
const object = Iterator.isObject({ key: "abc" });
const number = Iterator.isNumber(123);
const string = Iterator.isString("asdf");
const hasKey = Iterator.hasKey({ abc: "def" }, "abc");
```
