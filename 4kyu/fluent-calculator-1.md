# Fluent Calculator

链接：<https://www.codewars.com/kata/fluent-calculator-1>


## 题目介绍

Created into a new kata because of a certain limitation the Ruby kata posseses that this kata should also have if translated, which is what lead me to create a new one.

### Fluent Calculator Your task is to implement a simple calculator with fluent syntax

```js
var FluentCalculator = /* Magic */;
```

FluentCalculator should be separated in two, the `Values` and the `Operations`, one can call the other, but cannot call one of his own.

A `Value` can call an `Operation`, but cannot call a value

```js
FluentCalculator.one.plus
FluentCalculator.one.one // undefined, if you may.
```

An `Operation` can call a `Value`, but cannont call a operation

```js
FluentCalculator.one.plus.two // this should have a value of 3
FluentCalculator.one.plus.plus // If you replace 'one' with 'c', I could allow it. (undefined as well)
```

Pairs of `Value` and `Operation` should be stackable to infinity

```js
FluentCalculator.one.plus.two.plus.three.minus.one.minus.two.minus.four // Should be -1
```

A `Value` should resolve to a primitive integer

```js
FluentCalculator.one.plus.ten - 10 // Should be 1
```

### Now, the fun part... Rules

- eval is disabled
- `Values` in FluentCalculator should go from zero to ten.
- Supported `Operations` are plus, minus, times, dividedBy
- Rules mentioned above
  - FluentCalculator should be stackable to infinity
  - A `Value` can only call an `Operation`
  - An `Operation` can only call a `Value`
  - A `Value` should be resolvable to a primitive integer, if needed as such

## 解题思路

了解 Object prototype， defineProperty 或者 Proxy 的特性。

## 参考答案

我自己的解决方案有点 Low B，就不放出来了。

贴一个思路比较类似的，代码较为规整的解答：

```js
var Magic = function() {
  var value = 0;

  var operators = {
    'plus': (a, b) => a + b,
    'minus': (a, b) => a - b,
    'times': (a, b) => a * b,
    'dividedBy': (a, b) => a / b
  };

  var numbers = [
    'zero', 'one', 'two', 'three', 'four', 'five',
    'six', 'seven', 'eight', 'nine', 'ten'
  ];

  Object.keys(operators).forEach((operator) => {
    var operatorFunction = operators[operator];
    var operatorObject = {};

    numbers.forEach((num, index) => {
      Object.defineProperty(operatorObject, num, {
        get: () => value = operatorFunction(value, index)
      });
    });

    Number.prototype[operator] = operatorObject;
  });

  numbers.forEach((num, index) => {
    Object.defineProperty(this, num, {
      get: () => {
        value = index;
        return Number(index);
      }
    });
  });
}

var FluentCalculator = new Magic();
```


犀利答案推荐：

```js
var Magic = function(type, op){
  this.type = type;
  this.op = op;
};
Magic.prototype.toString = function(){
  return this.op().toString();
};
var MagicNumber    = i  => function() { return this.type == 'op' ? new Magic('n',  _ => this.op(i))       : undefined; };
var MagicOperation = op => function() { return this.type == 'n'  ? new Magic('op', x => op(this.op(), x)) : undefined; };

['zero','one','two','three','four','five','six','seven','eight','nine','ten'].forEach((prop, n) =>
  Object.defineProperty(Magic.prototype, prop, { get:  MagicNumber(n) })
);

Object.defineProperty(Magic.prototype, 'plus',      { get: MagicOperation((x, y) => x + y) });
Object.defineProperty(Magic.prototype, 'minus',     { get: MagicOperation((x, y) => x - y) });
Object.defineProperty(Magic.prototype, 'times',     { get: MagicOperation((x, y) => x * y) });
Object.defineProperty(Magic.prototype, 'dividedBy', { get: MagicOperation((x, y) => x / y) });

var FluentCalculator = new Magic('op', x => x);
```

