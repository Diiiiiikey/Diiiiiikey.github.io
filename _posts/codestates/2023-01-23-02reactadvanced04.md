---
layouts: post
title:  "useMemo"
categories: JS
tag: [codestates]
toc: true
sidebar:
    nav: "docs"
---

컴포넌트는 기본적으로 상태가 변경되거나 부모 컴포넌트가 렌더링이 될 때마다 리렌더링을 하는 구조

but, 잦은 리렌더링은 성능 저하의 원인

## useMemo

특정 값(value)를 재사용하고자 할 때 사용하는 Hook

```js
function Calculator({value}){

	const result = calculate(value);

	return <>
    <div>
      {result}
    </div>
  </>;
}
```
calculate가 복잡한 연산 함수라면, 렌더링을 할 때마다 이 함수를 호출하고, 그 때마다 오랜 시간이 소요될 것이다.

```js
import { useMemo } from "react";

function Calculator({value}){

	const result = useMemo(() => calculate(value), [value]);

	return <>
    <div>
      {result}
    </div>
  </>;
}
```
렌더링 마다 value값이 변하지 않는다면, value를 저장하고 불러오기만 하면 됨

---

### Memoization
---

기존에 수행한 연산의 결과값 저장 해두고, 동일한 입력이 들어오면 재활용하는 프로그래밍 기법

