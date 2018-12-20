# Binary multiple of 3

链接：<https://www.codewars.com/kata/binary-multiple-of-3>

## 题目介绍

In this kata, your task is to create a regular expression capable of evaluating binary strings (strings with only `1`s and `0`s) and determining whether the given string represents a number divisible by 3.

Take into account that:

- An empty string might be evaluated to true (it's not going to be tested, so you don't need to worry about it - unless you want)
- The input should consist only of binary digits - no spaces, other digits, alphanumeric characters, etc.
- There might be leading `0`s.

### Examples (Javascript)

- `multipleof3Regex.test('000')` should be `true`
- `multipleof3Regex.test('001')` should be `false`
- `multipleof3Regex.test('011')` should be `true`
- `multipleof3Regex.test('110')` should be `true`
- `multipleof3Regex.test(' abc ')` should be `false`

You can check more in the example test cases

### Note

There's a way to develop an automata (FSM) that evaluates if strings representing numbers in a given base are divisible by a given number. You might want to check an example of an automata for doing this same particular task here.

If you want to understand better the inner principles behind it, you might want to study how to get the modulo of an arbitrarily large number taking one digit at a time.


## 解题思路

```js
/* Breakdown, based on automata:

^ - start
( - outer grouping (to enfore start/end)
     - start in A
  0* - zero or more '0'
  ( - A
    1 - exit A on a 1 (enter B)
    ( - B
      1 - exit B on a 1 (enter A)
      | - or exit B on a 0 (enter C)
        01*0 - C must enter and exit on a 0, can have zero-or-more 1's
      )+ - repeat B
      1 - exit C then B on a 1
    ) - End B
  )* - repeat A
)* - repeat everything
$ - end
*/
```

## 参考答案

一句话代码解决方案，我的提交：

```js
const multipleOf3Regex = /^(0*(1(01*0)*1)*)*$/;
```

其他参考答案：

```js
const multipleOf3Regex = /^(0|1(01*0)*1)+$/;
```

```js
const multipleOf3Regex = /^(0*(1(1|(01*0)+1))*)*$/;

/* Breakdown, based on automata:
^ - start
( - outer grouping (to enfore start/end)
     - start in A
  0* - zero or more '0'
  ( - A
    1 - exit A on a 1 (enter B)
    ( - B
      1 - exit B on a 1 (enter A)
      | - or exit B on a 0 (enter C)
        01*0 - C must enter and exit on a 0, can have zero-or-more 1's
      )+ - repeat B
      1 - exit C then B on a 1
    ) - End B
  )* - repeat A
)* - repeat everything
$ - end
*/
```

## 拓展阅读

《边学边玩酷JS》正则表达式章节： <https://learn.js.cool/regexp/base.html>
