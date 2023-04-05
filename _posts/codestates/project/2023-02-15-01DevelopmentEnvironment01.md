---
layouts: post
title: "[FE]개발환경 구성"
categories: PROJECT
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

필요한 기술 스택

## 필수항목

- Node.js
- Node.js 패키지 매니저
- 버전 관리 시스템 / 형상 관리 시스템 + 원격 리포지토리 서비스
- 프론트엔드 프레임워크(라이브러리)
- CSS
- CSS 프레임워크(라이브러리)
- CSS 네이밍 컨벤션
- Create React App
- 린터

---

### Node.js

---

브라우저를 벗어나 다양한 운영체제에서 실행할 수 있는 JavaScript 런타임

JavaScript로도 백엔드 개발이 가능

배포 전 개발 단계에서 JavaScript로 번들링이나 최적화 등 개발 작업을 JavaScript로 가능

codestates에서는 Node.js LTS 버전 사용을 권장

---

### 패키지 매니저

---

여러 소프트웨어를 한꺼번에 모아 설치, 업그레이드, 설정, 삭제 등을 할 수 있는 소프트웨어 툴

Node.js에서 대표적 - npm과 yarn

---

### 버전 관리 시스템 + 원격 리포지토리 서비스

---

- 버전 관리 시스템 Git
- 원격 리포지토리 서비스 Github

---

### 프론트엔드 프레임워크(라이브러리)

---

React

create-react-app - React 18

---

### CSS

---

- CSS 네이밍 컨벤션
  - BEM
  - Utility-First(Tailwind, Bootstrap)
  - (위 둘은 좀 찾아봐야겠다)
- CSS 관리 방법
  - CSS-in-JS 라이브러리 사용, 컴포넌트로 묶어 관리 - Styled-Component, Emotion
  - Utility-First CSS: Tailwind CSS, Bootstrap
  - CSS 파일 따로 관리
  - SASS 사용
  - UI 프레임워크 사용(비추천): Material UI, Chakra UI, Radix UI
    - UI 프레임워크는 실제 개발에서 많이 사용하고, 개발 생산성에 도움. CSS를 충분히 학습할 수 없어서 Pre-Project, Main-Project에서 비추

---

### Create React App

---

쉽고 빠르게 React SPA를 개발할 수 있도록 여러 오픈소스를 묶어 제공하는 툴 체인

번들링이나 배포, 테스트를 위한 기본 설정

---

### 린터

---

문법 에러나 코드 스타일 규칙에 맞지 않는 코드를 찾아주는 툴

- eslint
- prettier

---

## 선택 항목

- HTTP 요청
- 상태 관리
- TypeScript
- 번들러
- 테스트 프레임워크

---

### HTTP 요청

---

API 요청/응답을 처리

FE 개발자 간 혼용하지 않고 하나만 사용

- Fetch API & isomorphic-fetch
- Axios
- React Query (TanStack Query)
- SWR

---

### 상태 관리

---

props-drilling 문제 및 상태의 효율적인 관리

FE 개발자 간 혼용하지 않고 하나만 사용

- Redux
- Recoil
- Zustand
- React Context API
- Mobx

---

### TypeScript

---

JavaScript는 동적으로 타입이 정해지는 프로그래밍 언어

개발이 고도화되면 될 수록 변수의 타입을 아예 정하거나, 타입 검사를 할 수 있는 툴이 필요해짐

TypeScript는 정적 타입 언어처럼 사용, 변수나 함수의 리턴값에 타입을 지정하여 해당 타입이 아니면 TypeScript를 JavaScript로 컴파일하지 않게 하고 에러

### 번들러

---

JavaScript로 컴파일 과정 필요

FE 개발자 간 혼용하지 않고 하나만 사용

- webpack
- esbuild
- vite
- parcel

---

### 테스트 프레임워크

---

- Jest, React Testing Library
- Cypress
