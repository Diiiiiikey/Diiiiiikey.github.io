---
layouts: post
title:  "JS 코딩앙마 중급 2"
categories: JS
tag: [코딩앙마, constructor, function, 생성자 함수, 함수]
toc: true
sidebar:
    nav: "docs"
---

## 생성자 함수

<ul>
<li>함수 이름의 첫 글자는 대문자</li>
<li>객체 리터럴을 여러번 해야할 때 사용한다.</li>
<li>생성자 함수는 new를 붙인다.</li>
</ul>

#### 예문

```js
function User(name, age){
    this.name = name;
    this.age = age
    this.sayName = function(){
        console.log(this.name);
    }
}

let user1 = new User('Mike', 30);
let user2 = new User('Jane', 22);
let user3 = new User('Tom', 17);
let user5 = new User('Han', 40);

user5.sayName(); // Han
```
객체 프로퍼티처럼 단축 프로퍼티와 function을 생략해봤지만 불가.

<br/>

#### 예문2

```js
function Item(title, price){
    this.title = title;
    this.price = price;
    this.showPrice = function(){
        console.log(`가격은 ${price}`원 입니다.);
    }
}

const Item1 = new Item('apple', 300);
const Item2 = new Item('banana', 500);
const Item3 = new Item('peach', 1000);
Item1.showPrice(); // 가격은 300원 입니다.
Item2.showPrice(); // 가격은 500원 입니다.
Item3.showPrice(); // 가격은 1000원 입니다.
```

<br/>

막간 switch문 연습
```js
let fruit = prompt('과일')
switch(fruit){
    case Item1.title :
        alert(`${Item1.price}원 입니다.`);
        break;
    case Item2.title :
        alert(`${Item2.price}원 입니다.`)
        break;
    case Item3.title :
        alert(`${Item3.price}원 입니다.`)
        break;
    default :
        alert('없다');
}
```