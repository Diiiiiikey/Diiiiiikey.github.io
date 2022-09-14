---
layouts: post
title:  "JS 코딩앙마 기초 3"
categories: JS
tag: [코딩앙마, 형변환]
toc: true
sidebar:
    nav: "docs"
---

## 형변환

```js
console.log(

    String(3), // 3
    String(true), // true
    String(false), // false
    String(null), // null
    String(undefined), // undefined
        
    Number("1234"), // 1234
    Number("fufuf"), // NaN
    Number(true), // 1
    Number(false), // 0

    Boolean(1), // true
    Boolean(1234), // true
    Boolean("good"), // true
    Boolean(0), // false
    Boolean(""), // false
    Boolean(null), // false
    Boolean(undefined), // false
    Boolean(NaN) // false
)
```
<br>
<br>

주의사항
```js
console.log(
    Number(null), // 0
    Number(undefined), // NaN
    Number(0), // false
    Number('0'), // true
    Number(''), // false
    Number(' '), // true
            
```