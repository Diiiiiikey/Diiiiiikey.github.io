---
layouts: post
title:  "JS 코딩앙마 중급 1"
categories: JS
tag: [코딩앙마, var, let, const, 변수]
toc: true
sidebar:
    nav: "docs"
---

## var, let, const

<ul>
<li>var는 한번 선언된 변수를 다시 선언할 수 있다. 덮어씌워짐</li>

<li>var는 선언하기 전에 사용할 수 있다.(호이스팅(위로 끌어올린 것처럼), 할당은 안됨)</li>

<li>호이스팅은 스포크 내부 어디서든 변수 선언이 최상위에 선언된것처럼 (let, const도 해당)</li>

<li>let과 const는 Temporal Dead Zone(TDZ)의 영향을 받으며 할당하기 전에 사용불가</li>

<li>변수의 생성과정 1. 선언, 2. 초기화, 3. 할당</li>

<li>var는 선언과 초기화가 동시에 된다.</li>

<li>const는 선언, 초기화, 할당이 동시에</li>

<li>var는 함수스코프 let, const는 블록스코프</li>

<li>블록스코프는 모든 코드블록 내에서 선언된 변수는 코드블록 내에서만 유효하다. 함수, if, for, while, try/catch 등</li>

<li>함수스코프는 함수 내에서 선언된 변수만 지역변수가 됨 나머지는 밖에서도 사용 가능</li>
</ul>

```js
var age;
age = 30;
console.log(age);

let name;
name = 'Mike';
console.log(name)

const gender = 'male';
console.log(gender);
```