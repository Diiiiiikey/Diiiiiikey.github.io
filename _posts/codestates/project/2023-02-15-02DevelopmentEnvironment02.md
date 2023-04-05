---
layouts: post
title: "[FE]프레임워크 선택 및 설치"
categories: PROJECT
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

Create React App

```
npx create-react-app {원하는 디렉터리 경로}
```

---

Redux <https://redux.js.org/tutorials/quick-start>

```
npm install @reduxjs/toolkit react-redux
```

---

Styled Component <https://styled-components.com/docs/basics#installation>

```
npm install --save styled-components
```

---

ESlint, Prettier

React에서 ESlint를 사용할 수 있게 돕는 관련 플러그인 설치

```
npm install -D eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-react eslint-plugin-react-hooks eslint-plugin-prettier eslint-config-prettier
```

코드스테이츠 권장 .eslintrc.json , .prettierrc.json 설정을 적용

새로운 파일 ( .eslintrc.json , .prettierrc.json) 을 생성하고, 아래 코드를 참고하여 기본 설정을 적용

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

ESLint, Prettier VSCode Extention 설치

---
