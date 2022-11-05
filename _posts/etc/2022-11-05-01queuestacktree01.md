---
layouts: post
title:  "Queue, Stack, Tree"
categories: JS
tag: [helloworldjavascript]
toc: true
sidebar:
    nav: "docs"
---

어떤 데이터의 구체적인 구현 방식은 생략한 채, 데이터의 추상적 형태와 그 데이터를 다루는 방법만을 정해놓은 것을 가지고 ADT(Abstract Data Type) 혹은 추상 자료형이라고 합니다. 

## 큐(queue)

<ul>
    <li>데이터를 넣을 수 있는 선형 자료형</li>
    <li>먼저 넣은 데이터가 먼저 나옴. FIFO(First in Frist Out)</li>
    <li>데이터를 넣는 enqueue, 데이터를 추출하는 dequeue 등 작업</li>
</ul>

```js
class Pratice {
    constructor() {
        this.arr = [];
    }
    en(i) {
        this.arr.push(i);
    }
    de(i) {
        return this.arr.shift();
    }
}

const praticeQueue = new Pratice();
praticeQueue.en(1);
praticeQueue.en(2);
praticeQueue.en(3);
console.log(praticeQueue.de());
```

## 스택(stack)

<ul>
    <li>데이터를 넣을 수 있는 선형 자료형</li>
    <li>나중에 넣은 데이터가 먼저 나옴. LIFO(Last in Frist Out)</li>
    <li>데이터를 넣는 push, 데이터를 추출하는 pop, 가장 나중에 넣은 데이터를 확인하는 peek 등 작업</li>
</ul>

```js
class Pratice {
    constructor() {
        this.arr = [];
    }
    pu(i) {
        this.arr.push(i);
    }
    po() {
        return this.arr.pop();
    }
    pe() {
        return this.arr[this.arr.length - 1];
    }
}

const praticeStack = new Pratice();
praticeStack.push(1);
praticeStack.push(2);
praticeStack.push(3);
console.log(praticeStack.po()); //3
```

## 트리(tree)

여러 데이터가 계층 구조 안에서 서로 연결된 형태를 나타낼 때 사용

<ul>
    <li>node - 트리 안에 들어있는 각 항목</li>
    <li>child node - 노드는 여러 자식 노드를 가질 수 있다.</li>
    <li>parent node - 노드 A가 노드 B를 가지고 있다면 A는 B의 부모</li>
    <li>root node - 트리의 가장 상층부</li>
    <li>leaf node - 자식 노드가 없는 노드</li>
    <li>ancestor node - 노드 A의 자식을 따라 내려갔을 때 노드 B에 도달한다면 A는 B의 조상</li>
    <li>descendant node - 노드 A가 노드 B의 조상일 때, 노드 B는 노드 A의 자손</li>
    <li>sibling node - 같은 부ㅗ 노드를 갖는 다른 노드</li>
</ul>

```js
class Pratice {
  constructor(content, children = []) {
    this.content = content;
    this.children = children;
  }
}

const tree = new Pratice('good', [
  new Node('better'),
  new Node('best', [
    new Node('Awesome!')
  ])
]);

function traverse(node) {
  console.log(node.content);
  for (let child of node.children) {
    traverse(child);
  }
}

console.log(traverse(tree)); // good better best Awesome!
```