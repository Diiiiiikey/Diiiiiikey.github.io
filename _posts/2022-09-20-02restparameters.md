---
layouts: post
title:  "JS 코딩앙마 중급 10"
categories: JS
tag: [코딩앙마, rest parameter, spread syntax]
toc: true
sidebar:
    nav: "docs"
---

## 나머지 매개변수

점 세개 ... 로 사용한다

```js
function showName(name){
    console.log(name);
}

showName('Mike');
showName('Mike', 'Tom'); // 'Mike'
showName(); // undefined
```
함수의 인수를 얻는 방법
1. arguments
2. 나머지 매개변수
지금은 여러 장점이 있는 나머지 매개변수를 쓰는 추세이다.(화살표함수에는 arguments가 없다.)


#### arguments

<ul>
<li>함수로 넘어 온 모든 인수에 접근</li>
<li>함수 내에서 이용 가능한 지역변수</li>
<li>length / index</li>
<li>Array 형태의 객체(Object)</li>
<li>배열의 내장 메소드 없음(forEach, map 등)</li>
</ul>

```js
function showNameA(name){
    console.log(arguments.length); // 2
    console.log(arguments[0]); // Mike
    console.log(arguments[1]); // Tom
}
showNameA('Mike', 'Tom');
```


#### 나머지 매개변수(Rest Parameter)

es6 환경에서는 가급적 나머지 매개변수를 사용하는 것을 권장

정해지지 않은 개수의 인수를 배열로 나타낼 수 있게 한다.

배열의 메소드 사용가능

```js
function showNameB(...names) {
    console.log(names);
}
showNameB(); // []
showNameB('Mike'); // ['Mike']
showNameB('Mike', 'Tom'); // ['Mike', 'Tom']
```


#### 예문 1

전달된 모든 수를 더해라
```js
function add(...numbers){
    let result = 0;
    numbers.forEach((num) => (result += num));
    console.log(result);
}

add(1, 2, 3); // 6
add(1, 2, 3, 4, 5, 6, 7, 8, 9, 10); // 55
```

reduce를 사용
```js
function add(...numbers){
    let result = add.reduce((prev, cur) => prev + cur);
    console.log(result);
}

add(1, 2, 3); // 6
add(1, 2, 3, 4, 5, 6, 7, 8, 9, 10); // 55
```


#### 예문 2

유저의 객체를 만들어 주는 생성자 함수

나머지 매개변수는 항상 마지막에
```js
function User(name, age, ...skills) {
     this.name = name;
     this.age = age;
     this.skills = skills;
 }

 const user1 = new User('Mike', 30, 'html', 'css');
 const user2 = new User('Tom', 20, 'JS', 'React');
 const user3 = new User('Jane', 40, 'Nothing');

console.log(user1); // {name: 'Mike', age: 30, skills: ['html', 'css']}
```

<br/>

## 전개구문(Spread syntax)

#### 전개구문: 배열

```js
let arr1 = [1,2,3];
let arr2 = [4,5,6];

let result = [...arr1, ...arr2];

console.log(result); // [1, 2, 3, 4, 5, 6]

let resultt = [0, ...arr1, ...arr2, 7,8,9];

console.log(resultt); //[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```


#### 전개구문: 복제

```js
let arr = [1,2,3];
let arr2 = [...arr]; // [1,2,3]

let user = {name: "Mike", age: 30};
let user2 = {...user};

user2.name = "Tom"

console.log(user.name); // "Mike"
console.log(user2.name); // "Tom"
```


#### 예문(배열)

arr1을 [4,5,6,1,2,3] 으로 만들기
```js
let arr1 = [1,2,3];
let arr2 = [4,5,6];

arr1.unshift(...arr2); // arr1 = [...arr2, ...arr1]; 처럼 더 간단하게
console.log(arr1);

// 순회하면서 넣으려면

arr2.reverse().forEach((num) => {
    arr1.unshift(num);
});
```

#### 예문(객체)

유저에 info와 fe, lang을 skill로 만들어서 넣기
```js
let user = {name: "Mike"};
let info = {age: 30};
let fe = ["JS", "React"];
let lang = ["Korean", "English"];

user = Object.assign({}, user, info, {
        skills : []
    },
);

fe.forEach((item) => {
    user.skills.push(item);
});
lang.forEach((item) => {
    user.skills.push(item);
});

console.log(user); // {name: 'Mike', age: 30, skills: ['JS', 'React', 'Korean', 'English']}
```

전개구문을 사용하면
```js
user = {
    ...user,
    ...info,
    skills: [...fe, ...lang],
}; // {name: 'Mike', age: 30, skills: ['JS', 'React', 'Korean', 'English']}
```