# Multi Line Task: Fizz Buzz

链接： <https://www.codewars.com/kata/593550e26d07549c5100004a>

## 题目介绍

You need to complete the FizzBuzz function:

- if `n` is divisible by `15`, return `'fizzbuzz'`
- if `n` is divisible by `5`, return `'buzz'`
- if `n` is divisible by `3`, return `'fizz'`
- otherwise, return `n` as a number

where `n` is a positive integer.

Requirement: Every line must have at most 3 characters, and total number of lines must be less than `25`.

## 解题思路

```js
f = n => (n%3 ? "" : "fizz") + (n%5 ? "" : "buzz") || n;
```

## 参考答案

正常答案：

```js
f=
n=>
(n%
3?
"":
"f\
iz\
z")
+(n
%5?
"":
"b\
uz\
z")
||n
```

Hack 答案：

```js
function require(s) {
  return {readFileSync:()=>''}
};


f = n => (n%3 ? "" : "fizz") + (n%5 ? "" : "buzz") || n;
```

---

有的时候解题，不一定非得按照规矩的条条框框。

