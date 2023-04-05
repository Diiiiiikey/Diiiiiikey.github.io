---
layouts: post
title: "[Custom Component]Component-Driven Developmen"
categories: REACT
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

## Component-Driven Development(CDD)

디자인과 개발 단계에서부터 재사용할 수 있는 UI 컴포넌트를 미리 디자인하고 개발

부품 단위로 UI 컴포넌트를 만들어 나가는 개발

컴포넌트 단위로 만들어 페이지를 조립하는 개발 방식인 상향식 개발

---

CSS 전처리기의 문제를 보완하기 위해 BEM, OOCSS, SMACSS 같은 CSS 방법론이 대두

방법론의 공통 지향점

- 코드의 재사용
- 코드의 간결화(유지 보수 용이)
- 코드의 확장성
- 코드의 예측성(클래스 명으로 의미 예측)

BEM이란 Block, Element, Modifier로 구분하여 클래스명을 작성, Block, Element, Modifier 각각 —와 \_\_로 구분.

```css
.header_navigation--navi-text {
  color: red;
}
```

Block: 전체를 감싸고 있는 블럭요소 - header
Element: 블럭이 포함하고 있는 한 조각 - navigation
Modifier: 블럭 또는 요소의 속성 - navi-text

but, 클래스명 선택자 장황, 마크업이 불필요하게 커짐, 재사용하려고 할 때마다 모든 UI 컴포넌트를 명시적으로 확장.

CSS-in-JS의 등장

CSS-in-JS에는 대표적으로 Styled-Component

Styled-Component는 기능적(Functional) 혹은 상태를 가진 컴포넌트들로부터 UI를 완전히 분리해 사용할 수 있는 아주 단순한 패턴을 제공

---

## Styled Components 설치

설치방법

```
# with npm
$ npm install --save styled-components

# with yarn
$ yarn add styled-components
```

여러 버전의 Styled Components가 설치되어 발생하는 문제를 줄여주는 방법

package.json에 추가

```
{
  "resolutions": {
    "styled-components": "^5"
  }
}
```

Styled Components를 사용할 파일로 불러오기

```
import styled from "styled-components"
```

---

## Styled Components 문법

```js
const BlueButton = styled.button`
  background-color: blue;
  color: white;
`;

export default function App() {
  return <BlueButton>Blue Button</BlueButton>;
}
```

React 컴포넌트 사용하듯이 사용

---

hover 등 효과 작성

```js
const Button = styled.button`
  &:hover{
    background-color : skyblue;
    color : blue
  }
```

---

### 컴포넌트 재활용

```js
const BigBlueButton(BlueButton)`
    padding: 10px;
    margin-top: 10px;
`;
```

재활용한 컴포넌트를 재활용할 수도 있다.

---

### Props 활용

Styled Component로 만든 컴포넌트도 React 컴포넌트처럼 props를 내려줄 수 있다.

---

#### 조건부 렌더링

```js
const Button1 = styled.button`
  background: ${(props) => (props.skyblue ? "skyblue" : "white")};
`;
```

버튼 컴포넌트에 skyblue 라는 props가 있는지 확인하고, 있으면 배경색으로 skyblue를, 없을 경우 white를 지정

---

#### Props 값으로 렌더링

```js
const Button1 = styled.button`
  background: ${(props) => (props.color ? props.color : "white")};
`;
```

논리연산자도 사용가능

```js
const Button1 = styled.button`
  background: ${(props) => props.color || "white"};
`;
```

#### 전역 스타일 설정

```js
import { createGlobalStyle } from "styled-components";
```

전역 스타일 설정

```js
const GlobalStyle = createGlobalStyle`
	button {
		padding : 5px;
    margin : 2px;
    border-radius : 5px;
	}
`;
```

전역 스타일 적용

```js
function App() {
  return (
    <>
      <GlobalStyle />
      <Button>전역 스타일 적용하기</Button>
    </>
  );
}
```
