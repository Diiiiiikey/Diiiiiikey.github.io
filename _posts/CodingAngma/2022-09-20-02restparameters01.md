---
layouts: post
title:  "전개구문"
categories: JS
tag: [코딩앙마, rest parameter, spread syntax]
toc: true
sidebar:
    nav: "docs"
---

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

---

<br/>

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

---

<br/>

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

---

<br/>

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