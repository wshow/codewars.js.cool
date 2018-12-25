# Beginner - Reduce but Grow

链接：<https://www.codewars.com/kata/beginner-reduce-but-grow>

## 题目介绍


Given and array of integers (x), return the result of multiplying the values together in order. Example:

```
[1, 2, 3] --> 6
```

For the beginner, try to use the reduce method - it comes in very handy quite a lot so is a good one to know.

Array will not be empty.


## 解题思路

我看到题目第一反应使用数组的 Reduce。

## 参考答案

一句话代码解决方案，我的提交：

```js
const grow = x =>
  x.reduce((r, i) => r * i, 1);
```


## 拓展阅读

《边学边玩酷JS》

- 正则表达式章节： <https://learn.js.cool/regexp/base.html>
- 数组章节： <https://learn.js.cool/base/array.html>
