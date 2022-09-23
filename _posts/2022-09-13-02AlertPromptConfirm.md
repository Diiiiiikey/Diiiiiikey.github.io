---
layouts: post
title:  "JS 코딩앙마 기초 2"
categories: JS
tag: [코딩앙마, alert, prompt, confirm]
toc: true
sidebar:
    nav: "docs"
---


## alret, prompt, confirm

alert: 알려줌<br/>
prompt: 입력받음<br/>
confirm: 확인받음<br/>


단점 스크립트 일시 정지, 스타일링 불가<br/>


```js
const name = prompt("이름을 입력하세요.");
alert(`안녕하세요, ${name}님. 환영합니다. `);
```
<html>
<img src="/assets/images/2022-09-13/name.png" width="500">

<img src="/assets/images/2022-09-13/name2.png" width="500">

<img src="/assets/images/2022-09-13/name3.png" width="500">
</html>

<br/>

```js
const date = prompt("예약일을 입력해주세요.", "2020-08-11");
```
prompt는 기본값을 설정할 수 있음

<br/>

<html>
<img src="/assets/images/2022-09-13/prompt date.png" width="500">
</html>

<br/>

```js
const isAdult = confirm("당신은 성인입니까?");
```

<html>
<img src="/assets/images/2022-09-13/isAdult.png" width="500">
</html>


