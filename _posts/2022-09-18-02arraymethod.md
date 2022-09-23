---
layouts: post
title:  "JS 코딩앙마 중급 7"
categories: JS
tag: [코딩앙마, array, array method, method]
toc: true
sidebar:
    nav: "docs"
---

## array method

#### arr.splice(n, m, x)

1. 배열의 특정요소를 지움,<br/>
n번째 부터 m개 지워라 x에 추가할 요소
```js
let arr = [1, 2, 3, 4, 5];
arr.splice(0 ,3, 6, 7);
console.log(arr); // [6, 7, 4, 5]
```

2. 아무것도 지우지 않고 추가하는 방법
```js
let arr = ["나는", "철수", "입니다."];
arr.splice(1, 0, "이곳의", "주인장");
console.log(arr); // ["나는", "이곳의", "주인장", "철수", "입니다."];
```
1부터 0개 삭제, index 1 앞에 들어간다.


3. 삭제된 요소를 반환하기도 한다.
```js
let arr = [1, 3, 5, 7, 9];
arr.splice(0, 3);
console.log(arr); // 7, 9
console.log(result); // 1, 3, 5
```

<br/>

#### arr.slice(n, m)

n부터 m까지 반환한다.<br/>
m은 포함하지 않고 반환한다.<br/>
m이 없으면 끝까지 반환한다.<br/>
만약 괄호안에 아무것도 없으면 배열을 복사한다.
```js
let arr4 = [2, 4, 6, 8];
const arr5 = arr4.slice(1, 4);
console.log(arr5);
```

<br/>

#### arr.concat()

인자로 주어진 배열이나 값들을 기존 배열에 합쳐서 새 배열을 반환한다.
```js
let arr = [1, 2];

arr.concat([3, 4]); [1, 2, 3, 4]
arr.concat([3, 4],[5, 6]); // [1, 2, 3, 4, 5, 6]
arr.concat([3, 4], 5, 6); // [1, 2, 3, 4, 5, 6]
```

<br/>

#### arr.forEach(fn)

배열의 반복<br/>
함수를 인수로 받는다.<br/>
함수는 세 개의 매개변수가 있으며 해당요소, 인덱스, 해당 배열 자체이다.<br/>
보통은 해당요소와 인덱스만 사용한다.
```js
let arrr = ["Mike", "Tom", "Jane"];

arrr.forEach((name, index) => {
    console.log(`${index + 1}, ${name}`);
}); // 1. Mike / 2. Tom / 3. Jane
```

<br/>

#### arr.indexOf() / arr.lastIndexOf()

문자열의 indexOf와 동일하다.<br/>
배열 안에 해당 값 발견하고 없으면 -1을 반환한다.<br/>
두번째 인수는 시작 위치를 의미한다.<br/>
arr.lastIndexOf는 배열의 끝에서 부터 탐색을 시작한다.
```js
let arrrr = [1, 2, 3, 4, 5, 1, 2, 3];
arrrr.indexOf(3) // 2
arrrr.indexOf(3, 3); // 7 
arrrr.lastIndexOf(3); // 7 
```

<br/>

#### arr.includes()

포함하고 있는지 확인
```js
let arrrr = [1, 2, 3, 4, 5, 1, 2, 3];

arrrr.includes(2); // true
arrrr.includes(6); // false
```

<br/>

#### arr.find(fn) / arr.findIndex(fn)

indexOf와 동일하게 배열 안에서 해당 값 찾는다.<br/>
하지만 보다 복잡한 연산이 가능하도록 함수를 인수로 받는다.<br/>
첫번째 true 값만 반환하고 끝<br/>
arr.find 은 찾는 값이 없다면 undefined을 반환한다.<br/>
arr.findIndex 는 찾는 값의 인덱스를 반환하며 없다면 -1을 반환한다.
```js
let arr = [1, 2, 3, 4, 5];

const result = arr.find(function(good){
    return good % 2 = 0;
});

// 화살표 함수로 만들면
const result = arr.find((good) => {
    return good % 2= 0;
});

console.log(result); // 2

// findIndex 라면
const result = arr.findindex((good) => {
    return good % 2 = 0;
});

console.log(result); // 1
```

<br/>

###### 예문

```js
let userList = [
    {name : "Mike", age : 30},
    {name : "Jane", age : 27},
    {name : "Tom", age : 10},
];

const userListResult = userList.find((user) => {
    if(user.age < 19){
        return true;
    }
    return false;
});

console.log(userListResult); // {name : "Tom", age : 10}

// 근데 사실 아래처럼 해도 됨
const userListResult = userList.find((user) => {
    return user.age > 19;
});
```

<br/>

###### 예문 2

```js
let userList = [
    {name : "Mike", age : 30},
    {name : "Jane", age : 27},
    {name : "Tom", age : 10},
];

const userListResult = userList.findIndex((user) => {
    if(user.age < 19){
        return true;
    }
    return false;
});

console.log(userListResult); // 2
```

<br/>

#### arr.filter(fn)

조건에 만족하는 모든 요소를 반환한다.
```js
let userList = [
    {name : "Mike", age : 30},
    {name : "Jane", age : 27},
    {name : "Tom", age : 10},
];

const userListResult = userList.filter((user) => {
    if(user.age > 19){
        return true;
    }
    return false;
});

console.log(userListResult); // {name: 'Mike', age: 30}, {name: 'Jane', age: 27}
```

<br/>

#### arr.reverse()

역순으로 재정렬<br/>
최근 가입된 유저, 가장 최근 글 순서로 정렬할 때 많이 쓰인다.

<br/>

#### arr.map(fn)

한수를 받아 특정 기능을 시행하고 새로운 배열을 반환한다.


매번 나이를 확인하는 것이 귀찮기 때문에 isAdult 라는 프로퍼티를 추가한 새로운 배열을 만든다.
```js
let userList = [
    {name : "Mike", age : 30},
    {name : "Jane", age : 27},
    {name : "Tom", age : 10},
];

let newUserList = userList.map((user, index) => {
    return Object.assign({}, user, {
        isAdult : user.age > 19
    });
});

console.log(newUserList); // [{name: 'Mike', age: 30, isAdult: true}, {name: 'Jane', age: 27, isAdult: true}, {name: 'Tom', age: 10, isAdult: false}

// index까지 사용한다면
let newUserList = userList.map((user, index) => {
    return Object.assign({}, user, {
        id : index + 1,
        isAdult : user.age > 19,
    });
});
```

<br/>

#### arr.join()

배열을 합쳐서 문자열을 만든다.<br/>
인수로 구분자를 받는다.
```js
let arrHi = ["안녕", "반가워"];
let resultHi = arrHi.join();
console.log(resultHi); // 안녕,반가워

let resultHi2 = arrHi.join(" ");
console.log(resultHi2); // 안녕 반가워
```

<br/>

#### arr.split

문자열을 나눠서 배열로 만든다.
```js
const users = "Mike, Jane, Tom, Tony";
const usersresult = users.split(",");

const lyrics = "She said What you know about love";
const lyricsresult = lyrics.split(" ")

const lyrics2 = "한국어로 한다면";
const lyricsresult2 = lyrics2.split("")

console.log(usersresult);// ['Mike', ' Jane', ' Tom', ' Tony']
console.log(lyricsresult);// ['She', 'said', 'What', 'you', 'know', 'about', 'love']
console.log(lyricsresult2);// ['한', '국', '어', '로', ' ', '한', '다', '면']
```

<br/>

#### Array.isArray()

배열인지 확인하는 방법<br/>
자바스크립트에서 배열은 객체형이기 때문에 typeOf는 객체라고 알려준다.
```js
let userList = [
    {name : "Mike", age : 30},
    {name : "Jane", age : 27},
    {name : "Tom", age : 10},
];

let to = typeof(userList);
console.log(to); // object

let too = Array.isArray(userList)
console.log(too); // true
```