---
layouts: post
title: "[OOP]프로토타입 체인"
categories: JS
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

## extends

```js
class Car {
  constructor(color) {
    this.color = color;
    this.wheels = 4;
  }
  drive() {
    console.log("drive..");
  }
  stop() {
    console.log("STOP!");
  }
}

class Bmw extends Car {
  park() {
    console.log("PARK");
  }
}

const z4 = new Bmw("blue");
```

Car를 상속받은 Bmw를 상속받은 z4
중간에 있는 Bmw에 속성이나 메소드를 추가하려면
extends를 사용해야한다.

## super(method)

부모에 있는 메소드와 같은 이름의 메소드를 추가하고 작동시키려면

```js
class Bmw extends Car {
  park() {
    console.log("PARK");
  }
  stop() {
    super.stop();
    console.log("stop");
  }
}

z4.stop(); // STOP! // stop 둘 다 작동
```

이것을 method overriding 이라고 한다.

## super(constructor)

Car의 상속을 받는 Bmw에 속성을 추가하려면

```js
class Bmw extends Car {
  constructor(color) {
    super(color);
    this.navigation = 1;
  }
}
```

와 같이 부모인 Car와 동일하게 constructor를 만들고 super를 든 뒤에 this를 적어주어야 한다.

```js
let div = document.createElement("div");

console.log(div.__proto__); // HTMLDivElement // prototype: HTMLElement
console.log(div.__proto__.__proto__); // HTMLElement // prototype: Element
console.log(div.__proto__.__proto__.__proto__); // Element // prototype: Node
console.log(div.__proto__.__proto__.__proto__.__proto__); // Node // prototype: EventTarget
console.log(div.__proto__.__proto__.__proto__.__proto__.__proto__); // EventTarget // prototype: Object
console.log(div.__proto__.__proto__.__proto__.__proto__.__proto__.__proto__); // Object // prototype: null
console.log(
  div.__proto__.__proto__.__proto__.__proto__.__proto__.__proto__.__proto__
); // null
```
