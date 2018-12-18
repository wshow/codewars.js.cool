# Multiples of 3 or 5

链接： <https://www.codewars.com/kata/multiples-of-3-or-5/javascript>

## 题目介绍

If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.

Finish the solution so that it returns the sum of all the multiples of 3 or 5 below the number passed in.

> Note: If the number is a multiple of both 3 and 5, only count it once.

Courtesy of ProjectEuler.net


## 解题思路

- 第一步，得到一个 0（或者1） 到 n 的数组
  - 1.1 长度为 n 的数组 `new Array(n)` 这样的数组是 `[empty * n]`， 无法进行 map / reduce 等遍历操作的
  - 1.2 创建可遍历的数组 `new Array(n).fill(0)`
  - 1.3 填充 0 到 n 的数组 `new Array(n).fill(0).map((_, i) => i)`
- 遍历数组，如果当前元素 i 符合条件，则累加，用数组的 `reduce` 方法

## 参考答案

一句话代码解决方案，我的提交：

```js
const solution = n => (n <= 0 ? 0 : // fix 题目中出现负数的用例
  new Array(n).fill(0)
    .map((_, i) => i)
    .reduce((result, i) => result + (i % 3 === 0 || i % 5 === 0 ? i : 0), 0)
);
```

## 拓展阅读

《边学边玩酷JS》数组章节： <https://learn.js.cool/base/array.html>


