---
layouts: post
title: "[Project Refactoring]Typography refactoring"
categories: Main-Project
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

리팩토링을 마친 Typographies 컴포넌트는

```js
import styled from "styled-components";

function Typographies({ text, variant, typoStyle, margin }) {
  return (
    <StyledFont as={variant} typoStyle={typoStyle} margin={margin}>
      {text}
    </StyledFont>
  );
}

const StyledFont = styled.span.attrs((props) => ({
  typoStyle: props.typoStyle,
}))`
  display: -webkit-box;
  overflow: hidden;
  -webkit-box-orient: vertical;
  text-overflow: ellipsis;
  word-wrap: break-word;
  width: 100%;
  margin: ${(props) => props.margin};
  padding: ${(props) => props.theme.typos[props.typoStyle].padding};
  max-width: ${(props) => props.theme.typos[props.typoStyle].width};
  height: ${(props) => props.theme.typos[props.typoStyle].height};
  color: ${(props) => props.theme.typos[props.typoStyle].color};
  font-weight: ${(props) => props.theme.typos[props.typoStyle].bold};
  font-size: ${(props) => props.theme.typos[props.typoStyle].size};
  white-space: ${(props) => props.theme.typos[props.typoStyle].space};
  -webkit-line-clamp: ${(props) => props.theme.typos[props.typoStyle].line};
  line-height: ${(props) => props.theme.typos[props.typoStyle].lineHeight};
  text-shadow: ${(props) => props.theme.typos[props.typoStyle].textShadow};
  background-color: ${(props) =>
    props.theme.typos[props.typoStyle].backgroundColor};
`;

export default Typographies;
```

그리고
theme

```js
const typos = {
  title_1: {
    size: fontSizes.title,
    bold: "bold",
    color: colors.tea_2,
    space: "nowrap",
  },
  title_2: {
    size: fontSizes.title,
    bold: "bold",
    height: sizes.h_s,
    line: 2,
  },
  title_3: {
    size: fontSizes.xl,
    bold: "bold",
    height: sizes.h_xs,
    lineHeight: fontSizes.xl,
  },
  title_4: {
    size: fontSizes.zl,
    bold: "bold",
  },
  carousel: {
    size: fontSizes.carousel,
    bold: "bold",
    color: colors.tea_2,
    space: "nowrap",
    textShadow: "-1px 0 white, 0 1px white, 1px 0 white, 0 -1px white",
  },
  commissions: {
    size: fontSizes.base,
    bold: "bold",
    height: sizes.h_xs,
  },
  commissionSub: {
    size: fontSizes.base,
    height: sizes.h_xxxxxl,
    lineHeight: fontSizes.xl,
  },
  commissionMain: {
    size: fontSizes.base,
    lineHeight: fontSizes.xl,
  },
  name: {
    size: fontSizes.l,
    bold: "bold",
    color: colors.tea_2,
  },
  name_2: {
    size: fontSizes.base,
    bold: "bold",
    color: colors.tea_2,
  },
  base: {
    size: fontSizes.base,
  },
  base_2: {
    size: fontSizes.content,
    bold: "bold",
    color: colors.gray_3,
  },
  date: {
    size: fontSizes.s,
    color: colors.gray_3,
  },
};
```

확실히 사용할 때는 간편하지만 자유롭게 커스텀할 수 없다보니 FormPage를 만드는 과정에서 이건 아니다 싶었다.

차라리 색상, 크기 등을 조절할 수 있도록 만들어야 겠다.

theme에 정의된 typos 를 기본으로 하고 여기에 정의되지 않은 typo에 대한 커스텀이라고 보면 될 것 같다.

color를 예로 들면

```js
<Typographies text="제목" typoStyle="title_4" color="gray_3" />
```

처럼 typoStyle은 그대로 사용하면서 color를 gray_3으로 하면

```js
const StyledFont = styled.span.attrs((props) => ({
  typoStyle: props.typoStyle,
  color: props.color,
}))`
  color: ${(props) =>
    props.color
      ? props.theme.colors[props.color]
      : props.theme.typos[props.typoStyle].color};
`;
```

props를 받으면서 props.color가 있다면 props.color를 color로 사용하고 없다면 typoStyle의 color를 사용하게 되는 코드를 작성했다.
