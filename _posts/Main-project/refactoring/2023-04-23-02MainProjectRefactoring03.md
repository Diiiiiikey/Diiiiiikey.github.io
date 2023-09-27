---
layouts: post
title: "[Project Refactoring]버튼 컴포넌트"
categories: Main-Project
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

theme과 함께 수정해야할 컴포넌트

1. Button
2. ImageComponent
3. Typography

---

## Button

1. 헤더

{% raw %}

```js
<Button
  text="로그아웃"
  handleClick={handleLogout}
  addStyle={{
    width: "w_m",
    margin: "0 1rem 0 0",
    height: "h_xxs",
    fontSize: "m",
    backgroundColor: "transparent",
  }}
/>
<Button
  text="로그인"
  handleClick={handleClickLogin}
  addStyle={{
    width: 'w_m',
    margin: '0 1rem',
    height: 'h_xxs',
    color: 'tea_2',
    fontSize: 'm',
    backgroundColor: 'transparent',
  }}
/>
<Button
  text="회원가입"
  handleClick={handleClickSignUp}
  addStyle={{
    width: 'w_m',
    height: 'h_xxs',
    margin: '0 2rem 0 0',
    fontSize: 'm',
    backgroundColor: 'transparent',
  }}
/>
```

{% endraw %}

헤더에는 이렇게 세개의 버튼이 있다. color와 margin을 어떻게 처리해야할까

theme

```js
const buttons = {
  header: {
    backgroundColor: "transparent",
    border: "none",
    size: "1rem",
    margin: "0 1rem 0 0",
  },
};
```

theme에 buttons 변수를 선언했고 header 객체를 할당했다.

기존 button 컴포넌트

```js
import styled from "styled-components";

function Button({ buttonType, text, handleClick, id, addStyle = {} }) {
  return (
    <StyledButton
      id={id}
      type={buttonType}
      onClick={handleClick}
      addStyle={addStyle}
    >
      {text}
    </StyledButton>
  );
}

const StyledButton = styled.button.attrs((props) => ({
  width: props.addStyle.width,
  height: props.addStyle.height,
  border: props.addStyle.border,
  borderRadius: props.addStyle.borderRadius,
  fontSize: props.addStyle.fontSize,
  backgroundColor: props.addStyle.backgroundColor,
  color: props.addStyle.color,
  row: props.addStyle.row,
  margin: props.addStyle.margin,
  padding: props.addStyle.padding,
  borderColor: props.addStyle.borderColor,
}))`
  max-width: ${(props) => props.theme.sizes[props.width] || "inherit"};
  height: ${(props) => props.theme.sizes[props.height]};
  border-radius: ${(props) =>
    props.theme.radiuses[props.borderRadius] || "0.25rem"};
  font-size: ${(props) => props.theme.fontSizes[props.fontSize]};
  background-color: ${(props) =>
    props.theme.colors[props.backgroundColor] || "#ececec"};
  grid-row: ${(props) => props.row || "inherit"};
  border: ${(props) => (props.border ? "solid 1px" : "none")};
  border-color: ${(props) => props.theme.colors[props.borderColor]};
  color: ${(props) => props.theme.colors[props.color]};
  margin: ${(props) => props.margin};
  padding: ${(props) => props.padding};
  font-weight: bold;
  white-space: nowrap;
  display: flex;
  justify-content: center;
  align-items: center;

  cursor: pointer;

  &:hover {
    filter: brightness(90%);
  }
  &:active {
    filter: brightness(70%);
    transform: translate(0, 1px);
  }
`;

export default Button;
```

하드코딩이나 다름이 없는 느낌

다시 만든 buttons 컴포넌트

```js
import styled from "styled-components";

function Buttons({ buttonType, text, handleClick, id, buttonStyle, color }) {
  return (
    <StyledButton
      id={id}
      type={buttonType}
      onClick={handleClick}
      buttonStyle={buttonStyle}
      color={color}
    >
      {text}
    </StyledButton>
  );
}

const StyledButton = styled.button.attrs((props) => ({
  buttonStyle: props.buttonStyle,
}))`
  background-color: ${(props) =>
    props.theme.buttons[props.buttonStyle].backgroundColor || "#ececec"};
  border: ${(props) => props.theme.buttons[props.buttonStyle].border};
  font-size: ${(props) => props.theme.buttons[props.buttonStyle].size};
  color: ${(props) => props.theme.colors[props.color]};
  margin: ${(props) => props.theme.buttons[props.buttonStyle].margin};
  font-weight: bold;
  white-space: nowrap;

  cursor: pointer;

  &:hover {
    filter: brightness(90%);
  }
  &:active {
    filter: brightness(70%);
    transform: translate(0, 1px);
  }
`;

export default Buttons;
```

불필요한 css를 삭제했고 color는 직접 props로 받았다.

margin은 theme으로 관리하지 않는게 나을 것 같다

최종 buttons 컴포넌트

```js
import styled from "styled-components";

function Buttons({
  buttonType,
  text,
  handleClick,
  id,
  buttonStyle,
  color,
  margin,
}) {
  return (
    <StyledButton
      id={id}
      type={buttonType}
      onClick={handleClick}
      buttonStyle={buttonStyle}
      color={color}
      margin={margin}
    >
      {text}
    </StyledButton>
  );
}

const StyledButton = styled.button.attrs((props) => ({
  buttonStyle: props.buttonStyle,
}))`
  ${(props) => console.log(props)};
  background-color: ${(props) =>
    props.theme.buttons[props.buttonStyle].backgroundColor};
  border: ${(props) => props.theme.buttons[props.buttonStyle].border};
  border-radius: ${(props) =>
    props.theme.buttons[props.buttonStyle].borderRadius};
  font-size: ${(props) => props.theme.buttons[props.buttonStyle].size};
  color: ${(props) =>
    props.theme.buttons[props.buttonStyle].color ||
    props.theme.colors[props.color]};
  padding: ${(props) => props.theme.buttons[props.buttonStyle].padding};
  margin: ${(props) => props.margin};
  font-weight: bold;
  white-space: nowrap;
  width: ${(props) =>
    props.theme.buttons[props.buttonStyle].width || "fit-content"};
  height: ${(props) =>
    props.theme.buttons[props.buttonStyle].height || "fit-content"};

  cursor: pointer;

  &:hover {
    filter: brightness(90%);
  }
  &:active {
    filter: brightness(70%);
    transform: translate(0, 1px);
  }
`;

export default Buttons;
```

theme

```js
const buttons = {
  header: {
    backgroundColor: "transparent",
    border: "none",
    size: fontSizes.m,
  },
  write: {
    backgroundColor: colors.tea_1,
    border: "none",
    size: fontSizes.m,
    color: colors.white,
    padding: "0.5rem 1.5rem",
    borderRadius: radiuses.base,
  },
  edit: {
    backgroundColor: colors.gray_2,
    border: "none",
    size: fontSizes.m,
    padding: "0.5rem 1.5rem",
    borderRadius: radiuses.base,
  },
  smallEdit: {
    backgroundColor: colors.white,
    size: fontSizes.m,
    border: `1px solid ${colors.gray_1}`,
    padding: "0.25rem 0.75rem",
    borderRadius: radiuses.half,
  },
  long: {
    backgroundColor: colors.tea_1,
    border: "none",
    size: fontSizes.m,
    color: colors.white,
    padding: "1rem 0",
    borderRadius: radiuses.base,
    width: "100%",
  },
};
```
