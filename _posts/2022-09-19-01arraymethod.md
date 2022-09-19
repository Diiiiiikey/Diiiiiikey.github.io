---
layouts: post
title:  "JS 코딩앙마 중급 8"
categories: JS
tag: [코딩앙마, array, array method, method]
toc: true
sidebar:
    nav: "docs"
---

## array method

#### arr.sort()

배열 재정렬<br/>
배열 자체가 변경되니 주의

```js
let arr = [1, 5, 4, 3, 6, 2];
arr.sort();

console.log(arr); // [1, 2, 3, 4, 5, 6]
```
```js
let arr = ["b", "c", "d", "a"];
arr.sort();

console.log(arr); // ["a", "b", "c", "d"]
```

하지만
```js
let arrr = [14, 55, 35, 74, 21];
arrr.sort();

console.log(arrr); // 14, 21, 36, 55, 74
```
값을 문자열 취급하기 때문에 십의 자리 숫자에 따른 정렬이 된다.

따라서 제대로된 정렬을 하기 위해서는 값을 비교해줄 수 있는 함수를 이용해야 한다.

작은 숫자부터 정렬하는 방법
```js
let arr = [27, 6, 88, 66, 2, 24];

function fn(a, b){
    return a - b ;
}
arr.sort(fn);
console.log(arr);

// 아래처럼 사용할 수도 있다.
arr.sort((a, b) => {
    return a - b;
});
console.log(arr); // [2, 6, 24, 27, 66, 88]
```
위와 같은 함수를 사용하기 보단 유용한 기능을 모아놓은 [Lodash](https://lodash.com)같은 라이브러리를 사용한다.<br/>
실무에서 많이 사용됨


#### arr.reduce(fn)

일수로 함수를 받는다.<br/>
((누적 계산값, 현재값) => {return 계산값}, 초기값)<br/>
초기값이 없으면 배열의 첫번째 요소가 들어간다.

arr.forEach() 를 사용한 배열의 모든 수 합치기
```js
let arr = [1, 2, 3, 4, 5];

let result = 0;
arr.forEach((num) => {
    result += num;
});

console.log(result); // 15
```

arr.reduce() 를 사용한 배열의 모든 수 합치기
```js
let arr = [1, 2, 3, 4, 5];

const result = arr.reduce((prev, cur) => {
    return prev, cur
}, 0);

console.log(result); // 15
```


###### 예문 1

reduce를 이용하여 성인들의 이름 구하기
```js
let userList = [
    { name : "Mike", age : 30 }, 
    { name : "John", age : 10 }, 
    { name : "Dave", age : 60 }, 
    { name : "Tom", age : 54 }, 
    { name : "Adell", age : 20 }, 
    { name : "Queen", age : 10 }, 
];

const result = userList.reduce((pr, cu) => {
    if(cu.age > 19){
        pr.push(cu.name);
    }
    return pr;
}, []);

console.log(result); // ['Mike', 'Dave', 'Tom', 'Adell']
```


###### 예문 2

reduce를 이용하여 나이의 합 구하기
```js
let userList = [
    { name : "Mike", age : 30 }, 
    { name : "John", age : 10 }, 
    { name : "Dave", age : 60 }, 
    { name : "Tom", age : 54 }, 
    { name : "Adell", age : 20 }, 
    { name : "Queen", age : 10 }, 
];

const result = userList.reduce((pr, cu) => {
    return (pr += cu.age);
}, 0);

console.log(result); // 184
```


###### 예문 3

reduce를 이용하여 이름이 4자인 사람 찾기
```js
let userList = [
    { name : "Mike", age : 30 }, 
    { name : "John", age : 10 }, 
    { name : "Dave", age : 60 }, 
    { name : "Tom", age : 54 }, 
    { name : "Adell", age : 20 }, 
    { name : "Queen", age : 10 }, 
];

const result = userList.reduce((pr, cu) => {
    if(cu.name.length = 4){
        pr.push(cu.name);
    }
    return pr
}, []);

console.log(result); // ['Mike', 'John', 'Dave']
```


#### arr.reduceRight()

reduce와 기능이 동일하지만 배열의 끝부터 연산을 수행한다.
