# Double Char

链接：<https://www.codewars.com/kata/double-char>

## 题目介绍

Given a string, you have to return a string in which each character (case-sensitive) is repeated once.

```
doubleChar("String") ==> "SSttrriinngg"

doubleChar("Hello World") ==> "HHeelllloo  WWoorrlldd"

doubleChar("1234!_ ") ==> "11223344!!__  "
```

Good Luck!

## 解题思路

我看到题目第一反应用正则。当然也可以使用数组的 Map。

## 参考答案

一句话代码解决方案，我的提交：

```js
const doubleChar = str =>
  str.split('')
  .map(i => i.repeat(2))
  .join('');
```


## 拓展阅读

《边学边玩酷JS》

- 正则表达式章节： <https://learn.js.cool/regexp/base.html>
- 数组章节： <https://learn.js.cool/base/array.html>
