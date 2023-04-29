---
layouts: post
title: "[Project Refactoring]input 컴포넌트"
categories: Main-Project
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

타이포그라피 리팩토링하는 과정에서 createTag의 input 컴포넌트가 말썽인걸 찾았다.

태그를 입력하고 엔터를 쳐서 여러 개의 태그를 설정할 수 있게 만들어 놨는데 엔터를 누르면 렌더링이 되고 모든 입력이 사라진다.

```js
const onKeyPress = (e) => {
  if (e.target.value.length !== 0 && e.key === "Enter") {
    submitTagItem();
    e.target.value = "";
  }
};
```

으로 엔터를 누르면 input에 있는 value를 submit하는 sumbitTagItem 함수를 실행하는데 이를

```js
const onKeyPress = (e) => {
  e.preventDefault();
  if (e.target.value.length !== 0 && e.key === "Enter") {
    submitTagItem();
    e.target.value = "";
  }
};
```

함수를 실행한 뒤에 e.preventDefault(); 를 통해서 재시작을 막았다.

하지만 엔터를 포함한 모든 키가 막혔다.

input 컴포넌트도 타이포그라피를 손보고 input도 제대로 손봐야겠다.
