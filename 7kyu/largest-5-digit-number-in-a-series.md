# Largest 5 digit number in a series

链接：<https://www.codewars.com/kata/51675d17e0c1bed195000001>

## 题目介绍

In the following 6 digit number:

> 283910

`91` is the greatest sequence of 2 consecutive digits.

In the following 10 digit number:

> 1234567890

`67890` is the greatest sequence of 5 consecutive digits.

Complete the solution so that it returns the greatest sequence of five consecutive digits found within the number given. The number will be passed in as a string of only digits. It should return a five digit integer. The number passed may be as large as 1000 digits.



## 参考答案

一句话代码解决方案，我的提交：

```js
const solution = d => +d.split('').reduce((r, _, i) =>
  (+d.substring(i, i + 5) > r ? +d.substring(i, i + 5) : r), 0);
```

其他方案：

```js
const solution = d => |d.split('').map((v, i, arr) =>
  arr.slice(i, i + 5).join('')).sort((a, b) => |b - |a)[0];
```

```js
const solution = d => {
  const arr = d.split('');
  let max = 0;
  for (let i = 0; i < arr.length - 4; i += 1) {
    const temp = ~~d.substring(i, i + 5);
    if (temp > max) {
      max = temp;
    }
  }
  return max;
};
```


## 拓展阅读

《边学边玩酷JS》

- 数组章节： <https://learn.js.cool/base/array.html>
