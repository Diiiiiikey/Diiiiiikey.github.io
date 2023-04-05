---
layouts: post
title: "[Custom Component]Storybook"
categories: REACT
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

## Storybook

UI개발도구

Component Driven Development를 지원하는 도구 중 하나인 Component Explorer(컴포넌트 탐색기) 등장

Storybook은 Component Explorer의 UI 개발 도구 중 하나

1. 재사용성을 확대하기 위해 컴포넌트를 문서화
2. 자동으로 컴포넌트를 시각화하여 시뮬레이션할 수 있는 다양한 테스트 상태 확인
3. 버그를 사전 방지
4. 테스트 및 개발 속도 향상
5. 애플리케이션 또한 의존성을 걱정하지 않고 빌드

Storybook에서 지원하는 주요 기능

- UI 컴포넌트들 카탈로그화
- 컴포넌트 변화를 Stories로 저장
- 핫 모듈 재 로딩과 같은 개발 툴 경험 제공
- 리액트를 포함한 다양한 뷰 레이어 지원

---

리액트 프로젝트 만들고

```js
npx create-react-app storybook-practice
```

설치

```js
npx storybook init
```

React가 아니더라도 다양한 프론트엔드 라이브러리에서 사용가능

실행

```js
npm run storybook
```

S3_Unit3_storybook 참고
