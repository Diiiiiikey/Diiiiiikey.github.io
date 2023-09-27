---
layouts: post
title: "[Virtual DOM]Diffing Algorithm"
categories: REACT
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

## React Diffing Algorithm

React가 기존 가상 DOM과 변경된 새로운 가상 DOM을 비교할 때, React는 새로운 가상 DOM 트리에 부합하도록 기존의 UI를 효율적으로 갱신하는 방법을 알아낼 필요가 있었다. 즉 하나의 트리를 다른 트리로 변형을 시키는 가장 작은 조작 방식을 알아내야만 했는데, 알아낸 조작 방식 알고리즘은 O(n^3)의 복잡도를 가지고 있다.

1000개의 엘리먼트라면 10억(1000^3)번의 비교 연산을 해야 함

이를 해결 하기 위해

React는 두 가지의 가정을 가지고 시간 복잡도 O(n)의 새로운 휴리스틱 알고리즘(Heuristic Algorithm)을 구현

1. 각기 서로 다른 두 요소는 다른 트리를 구축
2. key 프로퍼티로, 여러 번 렌더링을 거쳐도 변경되지 말아야 하는 자식 요소가 무엇인지 알 수 있음.

---

### React가 DOM 트리를 탐색하는 방법

---

비교할 때, 트리의 레벨 순서대로 순회하는 방식으로 탐색, 같은 레벨(위치)끼리 비교한다는 뜻, 너비 우선 탐색(BFS)의 일종

<html>
    <div style ="text-align:center">
        <img src= "https://user-images.githubusercontent.com/58800295/180724454-029225ae-7b24-4cec-bbed-2bc8171ed52c.png" alt="DOM" width="700" height="700">
    </div>
</html><br/>

---

### 다른 타입의 DOM 엘리먼트인 경우

---

HTML 태그에는 자식 태그와 부모 태그가 정해져 있는 특징(e.g. ul 태그 밑에 li 태그) 가 있기 때문에, 부모 태그가 달라진다면 React는 이전 트리를 버리고 새로운 트리 구축

```js
<div>
  <Change />
</div>
```

가

```js
<sapn>
  <Change/>
</span>
```

로 바뀐다면...

새로운 트리를 구축하기 때문에 이전의 DOM 노드들은 전부 파괴, span 태그 속 새로운 Change가 실행, state 또한 파괴

---

### 같은 타입의 DOM 엘리먼트인 경우

---

최대한 렌더링을 하지 않는 방향으로 최소한의 변경 사항만 업데이트

가능한 이유는 앞서 React가 실제 DOM이 아닌 가상 DOM을 사용해 조작하기 때문

Virtual DOM 내부의 프로퍼티만 수정, 모든 노드에 걸친 업데이트가 끝나면 실제 DOM으로의 렌더링을 시도

```js
<div className="before" title="stuff" />
```

가

```js
<div className="after" title="stuff" />
```

되면 className만 수정

className = before
{% raw %}

```js
 <div style={{color: 'red', fontWeight: 'bold"}} title="stuff" />
```

{% endraw %}

가

<br/>
className = after
{% raw %}

```js
<div style={{color: 'red', fontWeight: 'bold"}} title="stuff" />
```

{% endraw %}

되면 React는 color만 수정, 하나의 DOM 노드를 처리한 뒤 React는 뒤이어서 해당 노드들의 자식들을 순차적으로 동시에 순회하면서 차이가 발견될 때마다 변경. 이를 재귀적으로 처리한다고 표현

---

### 자식 엘리먼트의 재귀적 처리

---

```js
<ul>
  <li>first</li>
  <li>second</li>
</ul>
```

가

```js
<ul>
  <li>first</li>
  <li>second</li>
  <li>third</li>
</ul>
```

되면 자식 노드를 순차적으로 위에서부터 아래로 비교하면서 바뀐 점 탐색

React는 첫 번째 자식 노드들과 두 번째 자식 노드들이 일치하는 걸 확인한 뒤 세 번째 자식 노드를 추가

위에서 아래로 순차적으로 비교하기 때문에, 리스트 처음에 엘리먼트를 삽입하면 비효율적이다.

```js
<ul>
  <li>first</li>
  <li>second</li>
</ul>
```

가

```js
<ul>
  <li>zero</li>
  <li>first</li>
  <li>second</li>
</ul>
```

되면 first와 zero를 비교, 리액트는 전체가 바뀌었다고 판단, 전부 새롭게 렌더링된다.

따라서 key 속성 사용하여 이를 방지

---

#### key

---

```js
<ul>
  <li key="first">first</li>
  <li key="second">second</li>
</ul>
```

가

```js
<ul>
  <li key="zero">zero</li>
  <li key="first">first</li>
  <li key="second">second</li>
</ul>
```

되면 리액트는 zero가 생겼고 first와 second는 단지 위치 이동만 있었다는 것을 파악
