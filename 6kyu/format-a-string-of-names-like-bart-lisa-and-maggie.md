# Format a string of names like 'Bart, Lisa & Maggie'.

链接： <https://www.codewars.com/kata/format-a-string-of-names-like-bart-lisa-and-maggie>

## 题目介绍

Given: an array containing hashes of names

Return: a string formatted as a list of names separated by commas except for the last two names, which should be separated by an ampersand.

Example:

```js
list([ {name: 'Bart'}, {name: 'Lisa'}, {name: 'Maggie'} ])
// returns 'Bart, Lisa & Maggie'

list([ {name: 'Bart'}, {name: 'Lisa'} ])
// returns 'Bart & Lisa'

list([ {name: 'Bart'} ])
// returns 'Bart'

list([])
// returns ''
```

Note: all the hashes are pre-validated and will only contain A-Z, a-z, '-' and '.'.

## 解题思路

我看到题目第一反应用正则。

## 参考答案

一句话代码解决方案，我的提交：

```js
const list = names =>
  names.map(x=>x.name)
    .join(', ')
    .replace(/,\s(\w+)$/,' & $1');
```


## 拓展阅读

《边学边玩酷JS》正则表达式章节： <https://learn.js.cool/regexp/base.html>
