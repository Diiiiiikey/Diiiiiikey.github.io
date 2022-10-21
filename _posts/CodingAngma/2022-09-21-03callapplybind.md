---
layouts: post
title:  "call, apply, bind"
categories: JS
tag: [코딩앙마, call, apply, bind, method]
toc: true
sidebar:
    nav: "docs"
---

## call, apply, bind method

함수 호출 방식과 관계없이 this를 지정할 수 있음

#### call

모든 함수에서 사용할 수 있으며 this를 특정값으로 지정할 수 있다.
```js
const mike = {
    name : "Mike",
};

const tom = {
    name : "Tom",
};

function showThisName(){
    console.log(this.name);
}

showThisName(); // 이때 this는 window를 가리킨다. window.name은 빈문자열이다.

showThisName.call(mike); // Mike
```
함수를 호출하면서 call을 사용하고 this로 사용할 객체를 넘기면 해당 함수가 주어진 객체의 메소드인 것처럼 작동한다.


```js
const mike = {
    name : "Mike",
};

const tom = {
    name : "Tom",
};

function showThisName() {
    console.log(this.name);
}

function update(birthYear, occupation) {
    this.birthYear = birthYear;
    this.occupation = occupation;
}

update.call(tom, 1994, '학생');
console.log(tom); // {name: 'Tom', birthYear: 2000, occupation: '학생'}
```
call의 첫번째 매개변수는 this로 사용할 값(tom)이고 매개변수가 더 있으면 그 매개변수로 호출하는 함수(1994, '학생')로 전달된다.

---

<br/>

#### apply

apply 함수 매개변수를 처리하는 방법을 제외하면 call과 완전히 같다.<br/>

call은 일반적인 함수와 마찬가지로 매개변수를 직접 받지만 apply는 매개변수를 배열로 받는다.
```js
const mike = {
    name : "Mike",
};

function update(birthYear, occupation){
    this.birthYear = birthYear;
    this.occupation = occupation;
}

update.apply(mike, [1992, "선생"]);
console.log(mike); // {name: 'Mike', birthYear: 1992, occupation: '선생'}
```

---

<br/>

#### bind

함수의 this 값을 영구히 바꾼다.
```js
const mike = {
    name : "Mike",
};

function update(birthYear, occupation) {
    this.birthYear = birthYear;
    this.occupation = occupation;
}

const updateMike = update.bind(mike);
updateMike(1959, "백수");
console.log(mike); // {name: 'Mike', birthYear: 1959, occupation: '백수'}
```

---

<br/>

###### 예문 1

```js
const nums = [3, 10, 2, 40, 21]
const minNum = Math.min(nums)
const maxNum = Math.max(nums);

console.log(minNum); // NaN
console.log(maxNum); // NaN
```

배열을 풀어서 전달해야한다.
```js
const nums = [3, 10, 2, 40, 21]
const minNum = Math.min(...nums)
const maxNum = Math.max(...nums);

console.log(minNum); // 2
console.log(maxNum); // 40
```

apply 사용<br/>

두번째 매개변수로 배열을 전달하면 그 요소들을 차례대로 인수로 사용한다.
```js
const nums = [3, 10, 2, 40, 21]
const minNum = Math.min.apply(null, nums); // null 말고 this, 0, NaN 등 사용가능
const maxNum = Math.max.apply(null, nums);

console.log(minNum); // 2
console.log(maxNum); // 40
```

call 사용<br/>
call은 차례대로 들어와야하니까 ... 사용
```js
const minNum = Math.min.call(null, ...nums); 
const maxNum = Math.max.call(null, ...nums);

console.log(minNum); // 2
console.log(maxNum); // 40
```

###### 예문 2

```js
const user = {
    name: "Mike",
    showName: function(){
        console.log(`Hello, ${this.name}`);
    },
};

user.showName(); // Hello, Mike

let fn = user.showName;
fn(); // Hello, // fn에 할당할 때 this를 잃어버림

fn.call(user); // Hello, Mike
fn.apply(user); // Hello, Mike

let bindFn = fn.bind(user);
bindFn(); // Hello, Mike
```