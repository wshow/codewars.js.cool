# Base64 Encoding

链接：<https://www.codewars.com/kata/base64-encoding>

## 题目介绍

Extend the String object (JS) or create a function (Python, C#) that converts the value of the String to and from Base64 using the ASCII (UTF-8 for C#) character set.

Do not use built in functions.

Usage:

```js
// should return 'dGhpcyBpcyBhIHN0cmluZyEh'
'this is a string!!'.toBase64();

// should return 'this is a string!!'
'dGhpcyBpcyBhIHN0cmluZyEh'.fromBase64();
```

You can learn more about Base64 encoding and decoding here.

Note: This kata uses the non-padding version ("=" is not added to the end).

## 解题思路

了解 Buffer 模块即可。

## 参考答案

我的提交：

```js
String.prototype.toBase64 = function () {
  return new Buffer(`${this}`).toString('base64');
};

String.prototype.fromBase64 = function () {
  return new Buffer(`${this}`, 'base64').toString('ascii');
};
```

## 深入扩展

可以了解一下 Base64 算法的 js 实现。

```js
String.prototype.toBase64 = function() {
  var chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/';
  var encoded = '';

  for(var i=0; i < this.length; i+=3) {
    var c1 = this.charCodeAt(i),
        c2 = this.charCodeAt(i+1),
        c3 = this.charCodeAt(i+2);
    encoded += chars[(c1 & 0xFC) >> 2];
    encoded += chars[((c1 & 0x03) << 4) | ((c2 & 0xF0) >> 4)];
    encoded += chars[((c2 & 0x0F) << 2) | ((c3 & 0xC0) >> 6)];
    encoded += chars[c3 & 0x3F];
  }

  return encoded;
};

String.prototype.fromBase64 = function() {
  var chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/';
  var decoded = '';

  for(var i=0; i < this.length; i+=4) {
    var c1 = chars.indexOf(this[i]),
        c2 = chars.indexOf(this[i+1]),
        c3 = chars.indexOf(this[i+2]),
        c4 = chars.indexOf(this[i+3]);
    decoded += String.fromCharCode(((c1) << 2) | ((c2 & 0x30) >> 4));
    decoded += String.fromCharCode(((c2 & 0x0F) << 4) | ((c3 & 0xFC) >> 2));
    decoded += String.fromCharCode(((c3 & 0x03) << 6) | c4);
  }

  return decoded;
};
```
