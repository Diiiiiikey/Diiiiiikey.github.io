---
layouts: post
title:  "함수표현"
categories: JS
tag: [코딩앙마, function expressions, function declartion, arrow function]
toc: true
sidebar:
    nav: "docs"
---

#### 함수표현식

```js
let sayHello = function(){
    console.log('Hello');
}

sayHello();
```

<br/>

#### 함수선언문

```js
function sayHello(){
    console.log('Hello');
}

sayHello();
```

<br/>

함수선언문은 어디서든 호출이 가능하다.
```js
sayHello();

function sayHello(){
    console.log('Hello');
}
```

자바스크립트는 실행 전 초기화 단계에서 코드의 모든 함수를 생성해두기 때문에 코드 위치보다 위에서 호출이 가능하다. 이것을 호이스팅(hoisting)이라고 한다.

<br/>

#### 화살표함수

```js
let add = function(num1, num2){
    return num1 + num2;
}
```
위 함수를 화살표함수로 바꾸면

```js
let add = (num1, num2) => {
    return num1 + num2;
}
```
코드 본문이 한줄이고 return문이 있기 때문에 다음과 같이 return 생략 가능

```js
let add = (num1, num2) => (num1 + num2);
```
return문이 한줄이라면 괄호 생략 가능

```js
let add = (num1, num2) => num1 + num2;
```

<br/>

---

```js
let sayHello = function(name){
    return `Hello, ${name}`;
}
```
```js
let sayHello = (name) => {
    return `Hello, ${name}`;
}
```
```js
let sayHello = (name) => `Hello, ${name}`;
```
인수가 하나라면 괄호 생략 가능

```js
let sayHello = name => `Hello, ${name}`;
```

<br/>

```js
let showError = () => {
    alert('error!')
}
```
인수가 없는 함수는 괄호 생략 불가능

<br/>

return문 전에 여러 줄의 코드가 있다면 일반 괄호 사용불가
```js
let add = function(num1, num2){
    const result = num1 + num2;
    return result;
}
```

<br/>

#### 예문

```js
        // 함수선언문

const sayHello = function(name){
   const msg = `Hello, ${name}`;
   console.log(msg);
}
sayHello();

        // 화살표함수

let sayHello = (name) =>{
   const msg = `Hello, ${name}`;
   console.log(msg);
}
sayHello();
```

#### 예문2

```js
        // 함수선언문

const add = function(num1, num2){
    const result = num1 + num2;
    return console.log(result);
}

add(1, 3); // 4

        // 화살표함수

const add2 = (num1, num2) => console.log(num1 + num2);
add2(1, 2); // 3
```