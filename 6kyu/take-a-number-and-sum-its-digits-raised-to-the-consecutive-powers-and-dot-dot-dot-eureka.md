# ake a Number And Sum Its Digits Raised To The Consecutive Powers And ....¡Eureka!!

链接： <https://www.codewars.com/kata/take-a-number-and-sum-its-digits-raised-to-the-consecutive-powers-and-dot-dot-dot-eureka>

## 题目介绍

The number `89` is the first integer with more than one digit that fulfills the property partially introduced in the title of this kata. What's the use of saying "Eureka"? Because this sum gives the same number.

In effect: `89 = 8^1 + 9^2`

The next number in having this property is `135`.

See this property again: `135 = 1^1 + 3^2 + 5^3`

We need a function to collect these numbers, that may receive two integers a, b that defines the range [a, b] (inclusive) and outputs a list of the sorted numbers in the range that fulfills the property described above.

Let's see some cases:

```js
sumDigPow(1, 10) == [1, 2, 3, 4, 5, 6, 7, 8, 9]

sumDigPow(1, 100) == [1, 2, 3, 4, 5, 6, 7, 8, 9, 89]
```

If there are no numbers of this kind in the range [a, b] the function should output an empty list.

```js
sumDigPow(90, 100) == []
```

Enjoy it!!

## 解题思路

- 第一步，得到一个 a 到 b 的数组
  - 1.1 长度为 b-a 的数组 `new Array(b-a)` 这样的数组是 `[empty * n]`， 无法进行 map / reduce 等遍历操作的
  - 1.2 创建可遍历的数组 `new Array(b-a).fill(0)`
  - 1.3 填充 a 到 b 的数组 `new Array(b-a).fill(0).map((_, i) => a + i)`
- 选择数组中符合条件的结果集， 用数组的 `filter`（筛选）方法
  - 以 89 为例， 先将其拆分为数组 `[8, 9]`
  - 然后对数组进行操作，将每一位上进行计算累加， `8^1 + 9^2`， 依然使用数组的 `reduce` 方法
  - ECMAScript 新标准 `a ** b` 表示计算a的b次方

## 参考答案

一句话代码解决方案，我的提交：

```js
const sumDigPow = (a, b) =>
  new Array(b - a).fill(0)
    .map((_, i) => a + i)
    .filter(x =>
      `${x}`.split('')
        .reduce((result, n, i) => result + n ** (i + 1), 0)
      === x
    );
```

## 拓展阅读

《边学边玩酷JS》数组章节： <https://learn.js.cool/base/array.html>


