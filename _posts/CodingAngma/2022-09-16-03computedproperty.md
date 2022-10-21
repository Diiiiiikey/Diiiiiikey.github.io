---
layouts: post
title:  "계산된 프로퍼티"
categories: JS
tag: [코딩앙마, computed property, property, object, method]
toc: true
sidebar:
    nav: "docs"
---

## Computed property

```js
let a = 'age';

const user = {
    name : 'Mike',
    [a] : 30,
    [1 + 3] : 4,
}   
```
이때 age : 30를 [a] : 30 라고 사용할 수 있으며 [a]에는 변수 a에 할당된 값을 나타낸다. 이것을 computed property(계산된 프로퍼티) 라고 한다.

---

```js
const user = {
    [1 + 4] : 5,
    ["안녕" + "하세요"] : "Hello"
};
console.log(user); // {5 : 5, 안녕하세요 : "Hello"}
```
식 자체를 넣는 것도 가능하다.

```js
function makeObj(key, val){
    return {
        [key] : val, 
    }
}
const obj = makeObj("나이" , 33);
console.log(obj);
```
key에 무엇이 들어갈지 모를 때 유용
