---
layouts: post
title: "[State Managemen]Props Drillingt"
categories: REACT
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

상태란 동적으로 표현되는 데이터

Side Effect는 함수의 입력 외에도 함수의 결과에 영향을 미치는 요인. 대표적으로 네트워크 요청, API 호출

서로 다른 컴포넌트가 동일한 상태를 다룬다면, 출처는 오직 한 곳이어야 함(Single source of truth) - 원칙

따라서 전역상태 저장공간이 필요하다.

상태 관리를 위한 툴

- React Context
- Redux
- MobX

1. 전역 상태 저장소 제공
2. props drilling(프로퍼티 내려꽂기) 문제 해결 - A컴포넌트에 있는 상태를 A컴포넌트의 자손 자손 자손 자손 자손인 I컴포넌트가 필요로할 때, 중간에 있는 자손들은 상태를 필요로하지 않는다면 상태를 바로 I컴포넌트로 넘겨주는 방법

React로 사고하기만 잘 따라도 툴을 사용하지 않을 수 있다..

---

Props Drilling의 문제점

- 코드의 가독성 저하
- 코드의 유지보수 힘듬
- state 변경시 Props 전달 과정에서 불필요하게 관여된 컴포넌트들
- 리렌더링이 발생
- 성능 악영향

해결방법

- state 가까이 유지
- 상태관리 라이브러리 사용

---

시작하기 전에 반드시 컴포넌트 구조와, 데이터 흐름을 먼저 그림으로 그려봐야한다.

상태를 변경하는 함수를 내릴 수도 있다.

어떤함수가 어떤 역할을 하는지 파악부터하자.

주석을 활용하자.
