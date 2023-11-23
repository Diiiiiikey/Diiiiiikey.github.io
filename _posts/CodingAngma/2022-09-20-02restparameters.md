---
layouts: post
title: "나머지 매개변수"
categories: JS
tag: [코딩앙마, rest parameter]
toc: true
sidebar:
  nav: "docs"
---

## 나머지 매개변수

점 세개 ... 로 사용한다.

```js
function showName(name) {
  console.log(name);
}

showName("Mike");
showName("Mike", "Tom"); // 'Mike'
showName(); // undefined
```

함수의 인수를 얻는 방법

1. arguments
2. 나머지 매개변수

지금은 여러 장점이 있는 나머지 매개변수를 쓰는 추세이다.(화살표함수에는 arguments가 없다.)

<br/>

---

#### arguments

<ul>
<li>함수로 넘어 온 모든 인수에 접근</li>
<li>함수 내에서 이용 가능한 지역변수</li>
<li>length / index</li>
<li>Array 형태의 객체(Object)</li>
<li>배열의 내장 메소드 없음(forEach, map 등)</li>
</ul>

```js
function showNameA(name) {
  console.log(arguments.length); // 2
  console.log(arguments[0]); // Mike
  console.log(arguments[1]); // Tom
}
showNameA("Mike", "Tom");
```

---

<br/>

#### 나머지 매개변수(Rest Parameter)

es6 환경에서는 가급적 나머지 매개변수를 사용하는 것을 권장<br/>
정해지지 않은 개수의 인수를 배열로 나타낼 수 있게 한다.<br/>
배열의 메소드 사용가능

```js
function showNameB(...names) {
  console.log(names);
}
showNameB(); // []
showNameB("Mike"); // ['Mike']
showNameB("Mike", "Tom"); // ['Mike', 'Tom']
```

---

<br/>

##### 예문 1

전달된 모든 수를 더해라

```js
function add(...numbers) {
  let result = 0;
  numbers.forEach((num) => (result += num));
  console.log(result);
}

add(1, 2, 3); // 6
add(1, 2, 3, 4, 5, 6, 7, 8, 9, 10); // 55
```

reduce를 사용

```js
function add(...numbers) {
  let result = add.reduce((prev, cur) => prev + cur);
  console.log(result);
}

add(1, 2, 3); // 6
add(1, 2, 3, 4, 5, 6, 7, 8, 9, 10); // 55
```

<br/>

##### 예문 2

유저의 객체를 만들어 주는 생성자 함수<br/>
나머지 매개변수는 항상 마지막에

```js
function User(name, age, ...skills) {
  this.name = name;
  this.age = age;
  this.skills = skills;
}

const user1 = new User("Mike", 30, "html", "css");
const user2 = new User("Tom", 20, "JS", "React");
const user3 = new User("Jane", 40, "Nothing");

console.log(user1); // {name: 'Mike', age: 30, skills: ['html', 'css']}
```
