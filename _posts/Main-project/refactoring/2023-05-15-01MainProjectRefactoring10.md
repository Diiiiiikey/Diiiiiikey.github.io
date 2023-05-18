---
layouts: post
title: "[Project Refactoring]YourPage refactoring"
categories: Main-Project
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

```js
function ProfileModule({ info }) {
  return (
    <StyledContainer>
      <Buttons text="수정" buttonStyle="smallEdit" />
      <StyledImgContainer>
        {info.image ? (
          <Images src={info.image} alt="프로필 사진" />
        ) : (
          <StyledIcon />
        )}
      </StyledImgContainer>
      {info && (
        <>
          <Typographies text={info.nickname} typoStyle="name" />
          <Typographies
            text={`since ${info.createdAt.substr(0, 10)}`}
            typoStyle="base_2"
          />
        </>
      )}
    </StyledContainer>
  );
}
```

StyledIcon은

```js
import { MdAccountCircle } from "react-icons/md";
```

을 받아서

```js
const StyledIcon = styled(MdAccountCircle)`
  display: flex;
  font-size: 20rem;
  width: 100%;
`;
```

스타일 컴포넌트로 css를 설정했다.

기존에는 mui의 아이콘에 직접 font-size를 설정하는 방법으로 코드가 작성이 되어 있어서 반응형이 되지 않아서 다른 방법을 찾던 와중 우리 프로젝트에서 icon은 react icon 만 사용하기로 약속했었기 때문에 겸사겸사 react icon으로 바꾸면서 스타일 컴포넌트로 사이즈를 적용하는 방법을 찾아내서 적용시켰다.

