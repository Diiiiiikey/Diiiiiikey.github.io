---
layouts: post
title: "[Project Management] 개발환경 구성"
categories: JS
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

## 필수항목

- Node.js
- Node.js 패키지 매니저
  - npm
- 버전 관리 시스템 / 형상 관리 시스템 + 원격 리포지토리 서비스
  - 버전 관리 - Git
  - 원격 리포지토리 - Github
- 프론트엔드 프레임워크(라이브러리)
  - React 18
- CSS
  - CSS 프레임워크(라이브러리) - x
  - CSS 네이밍 컨벤션
    - Styled-Component
    - Utility-First CSS: Tailwind
    - CSS
    - SASS
- Create React App
- 린터
  - eslint
  - prettier

---

## 선택항목

- HTTP 요청
  - Fetch API & isomorphic-fetch
  - Axios
  - React Query (TanStack Query)
  - SWR
- 상태 관리
  - Redux
  - Recoil
  - Zustand
  - React Context API
  - Mobx
- TypeScript
- 번들러
  - webpack
  - esbuild
  - vite
  - parcel
- 테스트 프레임워크
  - Jest, React Testing Library
  - Cypress

---

Create React App

```
npx create-react-app {원하는 디렉터리 경로}
```

---

Redux

```
npm install @reduxjs/toolkit react-redux
```

---

Styled Component

```
npm install --save styled-components
```

---

ESlint, Prettier

```
npm install -D eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-react eslint-plugin-react-hooks eslint-plugin-prettier eslint-config-prettier
```

.eslintrc.json , .prettierrc.json 설정

---

```js
// .eslintrc.json
{
  "env": {
    "browser": true,
    "es2021": true
  },
  "extends": [
    "eslint:recommended",
    "plugin:react/recommended",
    "plugin:import/recommended",
    "plugin:jsx-a11y/recommended",
    "plugin:prettier/recommended"
  ],
  "parserOptions": {
    "ecmaFeatures": {
      "jsx": true
    },
    "ecmaVersion": "latest",
    "sourceType": "module"
  },
  "rules": {
    "react/react-in-jsx-scope": 0,
    "react/jsx-uses-react": 0
  }
}
```

```js
// .prettierrc.json
{
  "singleQuote": true
}
```
