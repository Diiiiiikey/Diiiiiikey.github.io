---
layouts: post
title: "[Project Refactoring]YourPage refactoring 2"
categories: Main-Project
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

기존에 YourPage는 하나의 페이지 안에 진행목록, 커미션목록, 프로필 지금은 없어진 채팅까지 세가지 모두 한번에 표현하려고 했다 그러다 보니 컨텐츠 하나하나가 여유가 없어보였다.

따라서 Header의 Account를 클릭하면 아코디언이 나오고 그곳에 프로필, 진행목록, 커미션목록, 로그아웃 까지 담아서 각 페이지로 연결하려 했다.

따라서 아코디언을 만들어야했고 모달 형태로 만들었다.

하지만 아코디언 바깥을 클릭했을 때 아코디언이 닫히는 것을 구현하는 데에 애를 먹었다.

기존에 배웠던 모달의 경우 모달창을 띄우고 페이지 전체를 덮는 background를 만들어서 그곳을 클릭하면 모달창이 닫히는 방식이었는데 이러한 방식으로 했을 경우에 모달창이 띄워져있는 동안 다른 곳과 상호작용을 할 수 없기 때문에 즉, 다른 곳을 클릭하고 싶으면 일단 background를 클릭하고 다시 한번 클릭을 해야하기 때문에 불편함이 생겼다.

한마디로, background를 사용하지 않고 외부를 클릭하면 닫히도록 만들어야 한다.

onBlur와 onFocus를 사용해봤지만 모달의 하위에 있는 프로필 등을 클릭하면 click 바로 focus가 풀려서 클릭이 되지 않고 닫히는 문제가 있었다.

궁극적으로 사용한 방법은

`document.body.addEventListener` 이다.

리액트에서 document를 직접적으로 건드는 것 좋은 방법이 아니란 것을 알지만 어쩔 수 없이 사용하기로 했다.

Header-HeaderAccount.jsx

```js
function HeaderAccount() {
  const [isOpen, setIsOpen] = useState(false);

  const handleClickAccount = () => {
    setIsOpen(!isOpen);
  };

  document.body.addEventListener("click", (e) => {
    if (e.target.offsetParent === undefined || e.target.offsetParent === null)
      return;
    if (e.target.offsetParent.id !== "accordion") {
      setIsOpen(false);
    }
    if (e.target.offsetParent.id === "accordion") {
      setIsOpen(false);
    }
  });

  return (
    <>
      <StyledYour onClick={handleClickAccount}>
        <StyledIcon />
      </StyledYour>
      {isOpen ? <Accordion /> : null}
    </>
  );
}
```

Header-HeaderAccount-Accordion.jsx

```js
<StyledAccordion id="accordion">
  <StyledButton onClick={handleClickProfile}>프로필</StyledButton>
  <StyledHr />
  <StyledButton onClick={handleLogout}>로그아웃</StyledButton>
</StyledAccordion>
```

handleClickAccount로 Accordion을 활성화 시킨다.

이때 Accordion 안에 있는 버튼들(프로필, 로그아웃) 등을 클릭할 때 e.target은 각각의 button이며 이들을 감싸고 있는 컴포넌트인 `StyledAccordion`에 id를 주어서 클릭했을 때 `e.target.offsetParent.id`로 접근 가능하도록 만들었다.

따라서

```js
if (e.target.offsetParent.id !== "accordion") {
  setIsOpen(false);
}
```

클릭했을 때 id가 accordion이 아니라면 닫음

```js
if (e.target.offsetParent.id === "accordion") {
  setIsOpen(false);
}
```

역시 id가 accordion 이어도 닫는다.

onBlur로 했을 때는 클릭이 안되고 닫혔는데 클릭이 되면서 닫히고 이 부분이 없으면 화면이동을 했을 경우에도 accordion이 닫히지 않고 남아있는다.

```js
if (e.target.offsetParent === undefined || e.target.offsetParent === null)
  return;
```

이 부분은 없어도 작동은 되지만 console에 오류로 뜨기 때문에 넣어주었다.
