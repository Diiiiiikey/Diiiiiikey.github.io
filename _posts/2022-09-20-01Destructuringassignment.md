---
layouts: post
title:  "JS 코딩앙마 중급 9"
categories: JS
tag: [코딩앙마, destructuring assignment, array destructuring]
toc: true
sidebar:
    nav: "docs"
---

## 구조분해할당(Destructuring assignment)

구조분해할당 구문은 배열이나 객체의 속성을 분해해서 그 값을 변수에 담응ㄹ 수 있게 하는 표현식이다.<br/>

#### 배열구조분해

```js
let [x, y] = [1, 2];

console.log(x); // 1
console.log(y); // 2
```

```js
let users = ["Mike", "Tom", "Jane"];
let [user1, user2, user3] = users;

console.log(user1); // "Mike"
console.log(user2); // "Tom"
console.log(user3); // "Jane"
```


문자열을 잘라서 배열을 반환하는 split을 이용
```js
let str = "Mike, Tom, Jane";
let [user1, user2, user3] = str.split(", ");

console.log(user1); // "Mike"
console.log(user2); // "Tom"
console.log(user3); // "Jane"
```


#### 배열구조분해: 기본값

```js
let [a, b, c] = [1, 2];

console.log(c); // undefined
```

따라서 기본값을 미리 세팅해서 에러를 방지한다.
```js
let [a=3, b=4, c=5] = [1, 2];

console.log(a); // 1
console.log(b); // 2
console.log(c); // 3
```

#### 배열구조분해: 일부 반환값 무시

, ,를 사용해서 공백을 만들어서 일부 반환값을 무시할 수 있다.
```js
let [user1, , user2] = ["Mike", "Tom", "Jane", "Tony"];

console.log(user1); // "Mike"
console.log(user2); // "Jane"
```


#### 배열구조분해: 바꿔치기

a와 b에 할당된 변수를 서로 바꾸는 방법
```js
let a = 1;
let b = 2;

let c = a;
a = b;
b = c;
```
처럼 해야하지만 구조분해 할당으로 간단하게 가능하다.
```js
[a, b] = [b, a];
```

<br/>

## 객체구조분해

```js
let user = {name: 'Mike', age: 30};

let {name, age} = user;
// let name = user.name;
// let age = user.age; 와 같다

// let {age, name} = user; 도 동일하게 작동

console.log(name); // "Mike"
ocnsole.log(age); // 30
```


#### 객체주고분해: 새로운 변수 이름으로 할당

```js
let {name : userName, age : userAge} = user;

console.log(userName); // "Mike"
console.log(userAge); // 30
```


#### 객체구조분해: 기본값

```js
let user = {name : 'Mike', age : 30, gender : 'female'};

let {name, age, gender = 'male'} = user;
```
객체에 gender 값이 있다면 그 값이 사용되고 없다면 male이 기본적으로 할당된다.