---
layouts: post
title: "[Project Refactoring]타이포그라피"
categories: Main-Project
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

기존 Typography 컴포넌트

```js
import styled from "styled-components";

function Typography({
  variant,
  text,
  size,
  color,
  bold,
  column,
  row,
  padding,
  flex,
  height,
  width,
  line,
  space,
  lineHeight,
  margin,
  textShadow,
}) {
  return (
    <StyledFont
      as={variant}
      size={size}
      color={color}
      bold={bold}
      column={column}
      row={row}
      padding={padding}
      flex={flex}
      height={height}
      width={width}
      line={line}
      space={space}
      lineHeight={lineHeight}
      margin={margin}
      textShadow={textShadow}
    >
      {text}
    </StyledFont>
  );
}

const StyledFont = styled.span.attrs((props) => ({
  size: props.size,
  color: props.color,
  bold: props.bold,
  column: props.column,
  row: props.row,
  padding: props.padding,
  margin: props.margin,
  flex: props.flex,
  height: props.height,
  line: props.line,
  space: props.space || "normal",
  width: props.width,
  lineHeight: props.lineHeight,
  textShadow: props.textShadow,
}))`
  display: -webkit-box;
  overflow: hidden;
  -webkit-box-orient: vertical;
  text-overflow: ellipsis;
  word-wrap: break-word;
  width: 100%;
  line-height: ${(props) => props.theme.fontSizes[props.lineHeight]};
  white-space: ${(props) => props.space};
  -webkit-line-clamp: ${(props) => props.line};
  height: ${(props) => props.theme.sizes[props.height]};
  max-width: ${(props) => props.theme.sizes[props.width]};
  font-size: ${(props) => props.theme.fontSizes[props.size]};
  padding: ${(props) => props.theme.paddings[props.padding]};
  margin: ${(props) => props.theme.margins[props.margin]};
  color: ${(props) => props.theme.colors[props.color]};
  font-weight: ${(props) => props.bold};
  grid-column: ${(props) => props.column};
  grid-row: ${(props) => props.row};
  flex: ${(props) => props.flex};
  text-shadow: ${(props) => props.textShadow};
`;

export default Typography;
```

사용할 때는

```js
<Typography
  variant="h2"
  text="인기 커미션"
  size="xl"
  bold="bold"
  space="nowrap"
  color="tea_2"
  padding="m"
/>
```

역시 하드코팅과 크게 다를게 없는 상태이다.

일단 title만 적용한 Typography

```js
import styled from "styled-components";

function Typographies({ text, variant, typoStyle }) {
  return (
    <StyledFont as={variant} typoStyle={typoStyle}>
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
  color: ${(props) => props.theme.typos[props.typoStyle].color};
  font-weight: ${(props) => props.theme.typos[props.typoStyle].bold};
  font-size: ${(props) => props.theme.typos[props.typoStyle].size};
  white-space: ${(props) => props.theme.typos[props.typoStyle].space};
  padding: ${(props) => props.theme.typos[props.typoStyle].padding};
`;

export default Typographies;
```

theme

```js
const typos = {
  title: {
    size: fontSizes.title,
    bold: "bold",
    color: colors.tea_2,
    space: "nowrap",
    padding: "1rem",
  },
};
```

사용할 때

```js
<Typographies text="새로운 커미션" typoStyle="title" variant="h2" />
```

사용할 때 코드가 훨씬 줄어들었다.
