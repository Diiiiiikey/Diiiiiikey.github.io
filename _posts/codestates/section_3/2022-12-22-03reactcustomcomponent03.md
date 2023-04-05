---
layouts: post
title: "[Custom Component]useRef"
categories: REACT
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

React는 DOM을 직접 건드리는 것을 금지한다.

React는 프론트엔드의 대부분을 구현할 수 있음 but,

DOM reference가 필요한 경우

- focus
- text selection
- media playback
- 애니메이션 적용
- d3.js, greensock 등 DOM 기반 라이브러리 활용

useRef는 DOM 노드, 엘리먼트, React 컴포넌트 주소값 참조가능

```js
const 주소값을_담는_그릇 = useRef(참조자료형);
// 이제 주소값을_담는_그릇 변수에 어떤 주소값이든 담을 수 있습니다.
return (
  <div>
    <input ref={주소값을_담는_그릇} type="text" />
    {/* React에서 사용 가능한 ref라는 속성에 주소값을_담는_그릇을 값으로 할당하면*/}
    {/* 주소값을_담는_그릇 변수에는 input DOM 엘리먼트의 주소가 담깁니다. */}
    {/* 향후 다른 컴포넌트에서 input DOM 엘리먼트를 활용할 수 있습니다. */}
  </div>
);
```

컴포넌트가 re-render되도 불면, 따라서 아래 제한된 상황에서 useRef 활용 가능

```js
function TextInputWithFocusButton() {
  const inputEl = useRef(null);
  const onButtonClick = () => {
    inputEl.current.focus();
  };
  return (
    <>
      <input ref={inputEl} type="text" />
      <button onClick={onButtonClick}>Focus the input</button>
    </>
  );
}
```
