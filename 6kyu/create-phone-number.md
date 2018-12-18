# Create Phone Number

链接： <https://www.codewars.com/kata/create-phone-number>

## 题目介绍

Write a function that accepts an array of 10 integers (between 0 and 9), that returns a string of those numbers in the form of a phone number.

Example:

```js
createPhoneNumber([1, 2, 3, 4, 5, 6, 7, 8, 9, 0])
// => returns "(123) 456-7890"
```

The returned format must be correct in order to complete this challenge.
Don't forget the space after the closing parentheses!

## 解题思路

我看到题目第一反应用正则。

- 首先输入的是 `10` 位数字的数组，转成字符串，然后使用正则替换。
- 正则表达式第一步，置空 `/^$/` 匹配开头结尾（科学严谨）
- 然后按照3-3-4拆分10位数字 `/^\d{3}\d{3}\d{4}$/`
- 用括号包裹，匹配替换 `/^(\d{3})(\d{3})(\d{4})$/`

## 参考答案

一句话代码解决方案，我的提交：

```js
const createPhoneNumber = n =>
  n.join('')
   .replace(/^(\d{3})(\d{3})(\d{4})$/, '($1) $2-$3');
```


## 拓展阅读

《边学边玩酷JS》正则表达式章节： <https://learn.js.cool/regexp/base.html>
