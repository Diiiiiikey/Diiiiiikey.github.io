---
layouts: post
title: "[Project Retrospect]230313~230319 2주차"
categories: Main-Project
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

## 230313 월요일

새로운 피그마를 바탕으로 css를 다시 만들기 시작했다.

멘토님께서는 컴포넌트같은 것들을 mui UI로 대체하는 것도 추천을 해주셔서 한번 살펴보기도 했다. 결국에는 그냥 우리가 컴포넌트를 만드는 것을 결정이 되었지만 아마도 도입을 했으면 다른 기능들에 집중을 할 수 있었을 것같다.

기존의 것을 거의 엎어버리고 다시 시작하는 마당에 또한 그렇게 잘하지도 못하는 주제에 너무 하고 싶어하는 것이 많았고 여전히 자만하고 있었던 것 같다.

### GRID

---

그리드 디스플레이를 사용하기로 했다.

<https://studiomeal.com/archives/533>

정리가 정말 잘되어 있는 블로그였다.

하지만 우리는 이것에 대해서도 더 깊게 생각했어야 했다. 그리드는 페이지 안에서의 각 요소의 위치를 잡아주고 그 안에서는 flex를 사용하는 것이 유리한 것 같다. 하지만 이때는 그걸 생각하지 못하고 무작정 모든 것을 grid로만 만들기 시작했다.

---

## 230314 화요일

기록을 보니 아마 이때부터였나 싶다. 한 팀원은 나에게 질문을 많이 하는 편이었다. 그러다 보니 차라리 코드를 보면서 알려주는 것이 편했고 그것은 결국 나에게도 그 팀원에게도 도움이 되는 방법이 아니었다.

서로가 맡은 부분에서 통일성은 있지만 자유롭게 코딩을 하는 것이 맞고 나는 내 입맛에 맞게만 코드를 작성하도록 만들었다. 심지어 아무말도 없이 다른 팀원의 코드를 바꾸기도 했다. 이것은 아주 큰 잘못이고 우리의 깃과 코드는 이때부터 복잡해지지 않았나 생각이 든다.

또한 이러한 방식으로 알려주며 하는 코딩은 나의 시간을 뺏으며 다른 팀원의 학습기회를 뺏는 좋지 않은 방법이라는 것을 거의 프로젝트의 막마지가 되었을 때 깨달았다.

### ComponentBox

---

컴포넌트 박스라는 것을 만들었다.

```jsx
import styled, { css } from "styled-components";

function ComponentBox({ mode, info }) {
  return (
    <>
      <StyledSummaryBox mode={mode}>
        <StyledImg src={info.image} alt={info.title} />
        <StyledTitle>{info.title}</StyledTitle>
        <StyledContent>{info.content}</StyledContent>
        <StyledSubtitle>{info.subtitle}</StyledSubtitle>
        <StyledWriter>{info.writer}</StyledWriter>
        <StyledDate>{info.date}</StyledDate>
      </StyledSummaryBox>
    </>
  );
}

export default ComponentBox;

const StyledImg = styled.img`
  max-width: 6rem;
  max-height: 3.75rem;
  grid-column: 1 / span 1;
  grid-row: 2 / span 3;
  align-self: center;
`;

const StyledTitle = styled.h2`
  grid-column: 1 / span 4;
  grid-row: 1 / span 1;
  font-size: 1.5rem;
  font-weight: bold;
`;

const StyledContent = styled.div`
  grid-column: 2 / span 3;
  grid-row: 2 / span 3;
  padding-left: 0.5rem;
  font-size: 1rem;
`;

const StyledSubtitle = styled.div`
  display: none;
`;

const StyledWriter = styled.div`
  display: none;
`;

const StyledDate = styled.div`
  display: none;
`;

const StyledSummaryBox = styled.div`
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(4, 1fr);
  max-width: 20rem;
  max-height: 7.5rem;
  padding: 0.5rem 1rem;
  gap: 0.5rem;
  border-radius: 4px;
  border: 1px solid #000;
  ${({ theme, mode }) => {
    console.log(theme);
    if (mode === "AUTHOR_COMMISSION_LIST") {
      return;
    }
    if (mode === "COMMISSION_SUB") {
      return css`
        max-width: 64rem;
        max-height: 13rem;
        padding: 1rem 2rem;
        column-gap: 2rem;
        row-gap: 1rem;
        ${StyledImg} {
          max-width: 15rem;
          max-height: 11.25rem;
          grid-column: 1 / span 1;
          grid-row: 1 / span 4;
          align-self: center;
        }
        ${StyledTitle} {
          grid-column: 2 / span 4;
          grid-row: 1 / span 1;
          font-size: 3rem;
        }
        ${StyledContent} {
          grid-column: 2 / span 4;
          grid-row: 2 / span 3;
          font-size: 1.5rem;
        }
      `;
    }
    if (mode === "REVIEW_LIST") {
      return css`
        grid-template-columns: repeat(12, 1fr);
        grid-template-rows: repeat(4, 1fr);
        max-width: 72rem;
        max-height: 5rem;
        ${StyledImg} {
          max-width: 4rem;
          max-height: 4rem;
          grid-column: 1 / span 2;
          grid-row: 1 / span 4;
        }
        ${StyledTitle} {
          display: none;
        }
        ${StyledContent} {
          grid-column: 2 / span 8;
          grid-row: 1 / span 4;
          font-weight: bold;
          padding-left: 1rem;
          border-left: 1px solid #000;
        }
        ${StyledWriter} {
          display: grid;
          grid-column: 11 / span 1;
          grid-row: 1 / span 4;
        }
        ${StyledDate} {
          display: grid;
          grid-column: 12 / span 1;
          grid-row: 1 / span 4;
        }
      `;
    }
    if (mode === "CHAT_LIST") {
      return css`
        grid-template-columns: repeat(6, 1fr);
        grid-template-rows: repeat(4, 1fr);
        max-width: 30rem;
        max-height: 5rem;
        border: 0;
        ${StyledImg} {
          max-width: 4rem;
          max-height: 4rem;
          grid-column: 1 / span 1;
          grid-row: 1 / span 4;
          align-self: center;
        }
        ${StyledWriter} {
          display: grid;
          grid-column: 2 / span 5;
          grid-row: 1 / span 2;
          padding-left: 0.5rem;
          font-size: 1rem;
        }
        ${StyledContent} {
          grid-column: 2 / span 5;
          grid-row: 3 / span 2;
          font-size: 1rem;
        }
        ${StyledTitle} {
          display: none;
        }
      `;
    }
    if (mode === "CHAT_COMMISSION_SUB") {
      return css`
        ${StyledTitle} {
          grid-column: 1 / span 1;
        }
        ${StyledSubtitle} {
          display: grid;
          grid-column: 1 / span 1;
          grid-column: 2 / span 4;
          font-size: 1.5rem;
          font-weight: bold;
        }
      `;
    }
    if (mode === "CHAT_COMMISSION_INFO") {
      return css`
        grid-template-columns: repeat(1, 1fr);
        grid-template-rows: repeat(6, 1fr);
        max-width: 12.25rem;
        max-height: fit-content;
        border: 0;
        padding: 0;
        ${StyledImg} {
          grid-column: 1 / span 1;
          grid-row: 1 / span 4;
          max-width: 12.25rem;
          max-height: fit-content;
        }
        ${StyledTitle} {
          grid-column: 1 / span 1;
          grid-row: 5 / span 1;
          max-height: fit-content;
        }
        ${StyledContent} {
          grid-column: 1 / span 1;
          grid-row: 6 / span 1;
          max-height: fit-content;
        }
      `;
    }
  }}
`;
```

하나의 jsx에 여러 개의 형태로 나올 수 있는 컴포넌트를 다 넣어놓았다. 그리드를 적용한 것이나 css를 mode에 맞게 다시 정의하는 것이 이상하긴 하지만 mode를 사용한 방식이 이상한 방법은 아닌것 같다. 모드 하나를 사용할 때 다른 모드를 정의한 곳에서도 렌더링이 일어날 줄 알았는데 확인해봤더니 그렇지는 않았다.

이 모드 자체를 theme으로 만들어서 사용하면 괜찮을 것같다.

---

## 230315 수요일

버튼컴포넌트와 인풋컴포넌트를 내 마음에로 수정했다. 이러면 안됐다. 이 프로젝트는 각자의 포트폴리오가 될 것이고 협업을 하는 과정을 담고 있다. 나는 우리 팀원을 조금 더 믿고 대화를 했어야했고 적어도 서로 코드를 맞추고 수정을 했어야 했다.

### Text Component

---

small text, text, title 세 가가지를 만들었다.

### Button component

---

멋대로 props로 backgroundcolor를 받게 수정했다. 우리는 이러한 문제를 직변하기 전에 버튼에 어떤 기능이 필요하고 어떠한 디자인으로 만들어야할지 미리 상의를 했어야 했다.

물론 멋대로 수정한 나의 잘못이 크다고 생각한다.

### Container

---

우리는 전역적으로 페이지에서 사용하자고 만든 컨테이너 컴포넌트가 있었다. width를 1280px이며 overflow-x가 hidden인.. 이러한 컴포넌트를 사용하는 게 옳은지도, 효율적인지도 확인해보지 않았고 다른 사람들이 이렇게 사용하는지도 모르고 그냥 프리 때는 이렇게 했으니까... 하고 도입한 것이다.

나는 이것을 한번 더 검증했어야하며 지금도 그냥 사용하고 있지만 더 나은 방법을 생각봐야한다.

아마 index.css만으로도 설정이 가능하지 않을까 싶지만 이 부분에서 우리 팀원에게 불만인 것은 컨테이너의 존재를 무시했다는 점이다. 분명히 말했다. 페이지의 코드를 작성할 때는 컨테이너 컴포넌트를 사용해달라고.. 존재 의미를 모르겠다면 나에게 말해주었으면 한번더 생각해봤을 것이고 다른 방법을 강구했을 수도 있다. 하지만 우리는 이러한 대화를 잘 하지 않았으며 나 또한 애써 다시 한번 말하지 않았다.

---

## 230316 목요일

2주가 지나고 서야 Github를 활용하기 시작했다. Issues를 작성하고 칸반을 만들고 마일스톤을 만들어봤지만 회고 초반에 말했듯 우리의 회의는 길지 않았다. 어떠한 방식으로 작성할 것인지 제대로 상의는 하지 않고 작성합시다!!!로 귀결하여 그냥 있기만 한 것들, 어쩌면 그냥 의미없이 귀찮은 것들이 추가된 형태가 되었다.

우리 팀은 잘 만들어진 수 많은 예시들을 놔두고 기능에 눈이 멀어 말처럼 앞만보고 달렸다. 똑바로 달렸으면 좋겠지만 그 마저도 아닌.. 잘 달리는 것도 아닌 어쩌면 달리는 것이 맞긴한가 싶은.. 그냥 팀원 서로가 보고싶은 앞만 봤던 것 같다.

### ComponentBox

---

컴포넌트 박스를 BoxComponents 폴더 안에 각각의 독립된 컴포넌트로 리팩토링했다.

---

지금 풀리퀘와 커밋의 내용을 보면서 기억을 더듬고 있는데 git flow가 한참 잘못되었다는 것을 다시 한번 깨닫는다. 내가 무엇을 했는지 알기가 힘들다..

---

## 230317 금요일

앞서 이미 잘못 진행되고 있는 부분들이 계속 이어지고 있다.

그리드, 커밋, 깃플로우 등 수정해야할 것은 그대로이며 여전히 그저 코드만 끄적이고 있었다.

멘토링을 통해서 우리가 어떠한 api를 통해서 어떠한 정보를 얻어야 하는지 제대로 이해하지 못하고 있었다는 사실을 깨달았다. api는 보통 백엔드에서 작성하지만 우리는 각 페이지에 어떠한 정보를 필요로하는지 충분한 대화를 하지 않았고 그저 백앤드에서 잘 해주기만 바랬었다. 나는 좀더 적극적으로 확인하고 요청했어야 했다.

### 상태관리

---

우리는 상태관리와 가공을 어떻게 해야하는지 필요한지 조차 제대로 파악하고 있지 않았다. 멘토님의 조언을 통해서 '리코일 + 리액트쿼리' 로 해보기로 했으며 이러한 사항은 코딩을 하기 전에 충분히 상의했어야 하는 부분이다.

---

1. 사이드이펙트 처리를 어떻게 할 것인시 상의
   - useEffect를 사용했다.
2. 배포를 먼저 해보는 것이 어떤가
   - 했어야했다.. 배포할 때 엄청 애먹었다.
3. 로그인 해야보이는 페이지 구분
   - 친구의 도움으로 구현했다.
4. 마무리할 때 pagespeed insights를 해보자
   - 해보고 포트폴리오에 추가를 해보자
5. 컴포넌트 폴더 대문자로 시작
   - git mv를 사용했어야 했다. 여기서 git flow는 더욱 나락으로 가고 말았다.
6. attrs 적용 - 무슨 역할인지 확인해보자
   - 적용을 했으나 정확히 어떠한 차이점이 있는지 찾아보자
7. mui의 타이포그래피 참고
   - mui의 typography를 참고하여 비슷하게 만들기 위해 노력했지만 theme의 사용법이 잘못되었다. 색상, 두께, 크키 등을 일일히 입력해야했다. title을 지정하면 title에 맞는 디자인이 나오도록 수정을 해보자
8. rem을 사용할거면 모든 단위를 rem으로
   - 진짜 탓하기 싫은데 왜 안바꿔주는 것입니까.. 우리 팀원들아
9. index.js에 레이지 로딩

- 그냥 까먹고 있었다. 왜 필요한지 찾아보고 적용해야 겠다.

10. 로그아웃시
    ```
    window.localStorage.clear()
    axios.defaults.headers.Authorization = null
    ```
11. 디바운스/trottle
    - 뭐였는지 기억이 안나니 찾아보자 - (사용자 인터랙션 경험의 극대화와 컴퓨팅 리소스의 절약을 위해 Debouncing 기법을 사용했습니다.)
12. 배포는 s3 -> frontcloud -> route53
    - 배포할 때 애먹은 부분 중 하나... 서버가 http라면 그냥 배포하자.. https로 부탁을 미리! 하던가

등의 조언을 받았다

알치고 확실하고 정말 도움이 되는 조언이었으나 받아들이고 적용하기 위한 여유가 없었다. 당장 눈앞의 문제를 해결하고 기능을 구현해야 된다는 압박에 css나 api만을 생각하고 있었다.

우리 멘토님께서는 기능을 구현하는 것보다 말이 안되는 것을 하지 않고 기본적인 것만 잘하면 된다. 라는 말씀을 처음에 하셨다. 우리는 정확히 반대되는 방향으로만 나아가고 있었다.

기능구현에만 몰두했고 git flow는 망가져가고 제대로된 협업이 되지 않고 있고 폴더명, 변수명 같은 기본적인 것도 제대로 지켜지지 않고 있었다. 딱... 하지 말라는 것만 하는 청개구리들이었다.

---

## 230318~230319 토, 일요일

디자인을 통일하고 싶은 마음에 주말동안 전체적인 css를 만진다고 선언후 css에 몰두했다. 이것은 배포 후에 했어도 됐고 주요한 기능이 만들어진 다음에 했어도 됐다. 해결해야하는 문제이긴 했지만 너무 일렀고 알리긴 했지만 다른 사람의 코드를 건드는 일이었기 때문에 나는 좀더 신중하게 결정하고 팀원들과 함께 리팩토링을 했어야 했다.

# 이 주차 한줄 평

오만방자함, 협업을 제대로 이해하지 못한 행동들의 연속
