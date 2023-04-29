---
layouts: post
title: "[Project Refactoring]image 컴포넌트"
categories: Main-Project
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

기존 imageComponent

```js
import styled from "styled-components";

function ImageComponent({ src, alt, imgStyle, width }) {
  return (
    <StyledContainer>
      <StyledImg src={src} alt={alt} imgStyle={imgStyle} width={width} />
    </StyledContainer>
  );
}

const StyledContainer = styled.div.attrs((props) => ({
  imgStyle: props.imgStyle,
}))`
  display: flex;
  align-items: center;
  grid-column: ${(props) => props.column};
  margin: ${(props) => props.theme.margins[props.margin]};
  aspect-ratio: ${(props) => props.theme.imgStyles[props.imgStyle]};
  flex: ${(props) => props.flex};
  height: auto;
  object-fit: cover;
`;

const StyledImg = styled.img.attrs((props) => ({
  imgStyle: props.imgStyle,
  width: props.width,
}))`
  display: flex;
  width: ${(props) => props.theme.imgSizes[props.width]};
  height: auto;
  aspect-ratio: ${(props) => props.theme.imgStyles[props.imgStyle]};
  object-fit: cover;
  border-radius: 0.5rem;
`;

export default ImageComponent;
```

뭔가 중복되는 코드도 있고 grid, flex와 같은 불필요한 css도 포함되어 있는 상태이다.

또한 commission 컴포넌트에서 반응형도 적응이 안되고 있었다.

images

```js
import styled from "styled-components";

function Images({ src, alt, imgStyle }) {
  return <StyledImg src={src} alt={alt} imgStyle={imgStyle} />;
}

const StyledImg = styled.img.attrs((props) => ({
  imgStyle: props.imgStyle,
}))`
  display: flex;
  width: 100%;
  align-items: center;
  height: auto;
  object-fit: cover;
  aspect-ratio: ${(props) => props.theme.images[props.imgStyle].imgStyle};
  border-radius: ${(props) => props.theme.images[props.imgStyle].imgStyle};
  border-radius: ${(props) => props.theme.images[props.imgStyle].borderRadius};
  max-width: ${(props) => props.theme.images[props.imgStyle].width};
  border: ${(props) => props.theme.images[props.imgStyle].border};
`;

export default Images;
```

새로운 이미지 컴포넌트는 styled component가 꽤 많이 짧아졌다.

또한 commission의 반응형도 적용된다.

theme

```js
const images = {
  commissions: {
    imgStyle: imgStyles.commission,
    width: sizes.w_xxl,
    borderRadius: radiuses.base,
  },
  commission: {
    imgStyle: imgStyles.commission,
    width: sizes.w_m,
    borderRadius: radiuses.base,
  },
  carousel: {
    imgStyle: imgStyles.carousel,
    width: sizes.w_xxxxxl,
    borderRadius: radiuses.base,
  },
  postSmall: {
    imgStyle: imgStyles.commission,
    width: sizes.w_xl,
    borderRadius: radiuses.base,
    border: "1px solid #cecece",
  },
  user: {
    imgStyle: imgStyles.user,
    width: sizes.w_xs,
  },
  user_2: {
    imgStyle: imgStyles.user,
    width: sizes.w_xxl,
  },
};
```

사용할 때에는

```js
<Images
  imgStyle="postSmall"
  src={info.commission.imageUrl[1]}
  alt={info.commission.title}
/>
```

사용할 때 짧은게 최고인 것 같다.
