---
layouts: post
title:  "객체 메소드"
categories: JS
tag: [코딩앙마, object method]
toc: true
sidebar:
    nav: "docs"
---

#### Object.assign()

객체 복제
```js
const user = {
    name : "Mike",
    age : 30,
}

const newUser = Object.assign({}, user);

newUser.name = "Tom";
console.log(user); // {name : 'Mike', age : 30}
console.log(newUser); // {name : 'Tom', age : 30}
```
빈 객체는 초기값이며, 두번째 매개 변수부터 들어온 객체들이 초기값에 병합되는 구조이다.

```js
const newUser2 = Object.assign({ gender : 'male' }, user);
```
성별 값만 있는 객체에 user를 병합하여 newUser2는 이름, 나이, 성별까지 3개의 프로퍼티를 가지게 된다.

```js
const newUser3 = Object.assign({ name : 'DK' }, user);
```
이름이 DK인 객체에 user가 병합되는 구조이기 때문에 이름은 user의 이름인 Mike가 된다.

```js
const newUser4 = {
    name : 'SB',
}

const info1 = {
    [a] : 20,
}

const info2 = {
    gender : 'male',
}

Object.assign(newUser4, info1, info2);

console.log(newUser4)
```
newUser4에 info들을 추가하는 방법

---

<br/>

#### Object.keys()

키 배열 반환
```js
const user = {
    name : "Mike",
    age : 30,
    gender : "male",
}

const result = Object.keys(user);
console.log(result); // ['name', 'age', 'gneder']
```

---

<br/>

#### Object.values()

값 배열 반환
```js
const user = {
    name : "Mike",
    age : 30,
    gender : "male",
}

const result = Object.values(user);
console.log(result); // ['Mike', 30, 'male']
```

---

<br/>

#### Object.entries()

키/값 배열 반환
```js
const user = {
    name : "Mike",
    age : 30,
    gender : "male",
}

const result = Object.entries(user);
console.log(result);
// ['name', 'Mike'], ['age', 30], ['gender', 'male']
```

---

<br/>

#### Object.fromEntries()

키/값 배열을 객체로
```js
const arr = [
    ["name", "Mike"],
    ["age", 30]
];

const result = Object.fromEntries(arr);
console.log(result);
// {name : "Mike", age : 30}
```
