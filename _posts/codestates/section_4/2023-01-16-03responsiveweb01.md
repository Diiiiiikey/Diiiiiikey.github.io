---
layouts: post
title: "[BROWSER]resposive wep"
categories: HTML CSS
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

## 반응형 웹

브라우저의 크기(스크린의 크기, 디바이스의 종류)에 실시간으로 반응, 크기에 따라 레이아웃이 변하는 웹 사이트

모바일 퍼스트(mobile first) - 사용자 경험(UX)을 디자인할 때 모바일일 경우에 최우선으로 초점을 맞춰 디자인

---

### 반응형 웹의 특징

하나의 URL을 기반으로 화면이 바뀜, 최적화된 페이지로 연결되는 별도의 URL이 있다면 반응형 웹이 아님(m.naver.com)

1. 효율적인 유지보수
2. 검색엔진(SEO) 최적화 유리
3. 사이트의 속도 저하
4. 웹브라우저 호환성 문제

---

### 미디어 쿼리

미디어 타입으로 단말기 종류에 따라 각각 다른 스타일을 적용

---

#### 적용법

head 태그 안에 link 태그, 미디어 속성을 사용하여 조건을 지정

```html
<link
  href="css파일이름.css"
  media="screen and (min-width: 400px) and (max-width: 1000px)"
  rel="stylesheet"
/>
```

head 태그 안 style 태그

```html
<style
  type="text/css"
  media="screen and (min-width: 400px) and (max-width: 1000px)"
>
  /* css를 작성 */
</style>
```

CSS 파일 혹은 태그 안에서 직접 미디어 쿼리 작성

---

#### 미디어 쿼리 구문 작성

```css
@media 미디어 타입 (조건(너비 및 높이)) {
    (CSS)
}

--예제
@media screen (max-width: 400px) {
    body {
			color: red;
		}
}
```

- 미디어 타입 - 어떤 미디어를 위한 것인지 브라우저
- 조건(너비 및 높이) - 지정한 창의 너비나 높이를 기준으로 만족되면 스타일 적용
- CSS - 조건 통과 후 스타일이 적용

---

#### 미디어 타입(Media Type)

- all - 모든 미디어 타입
- print - 프린터
- screen - 컴퓨터 화면
- speech - 스크린 리더
- ...
- screen이 대부분

---

#### 조건(너비 및 높이)

뷰포트 너비 가장 많이 사용

뷰포트가 특정 너비 이상 또는 이하인 경우 CSS를 적용

min-width, max-width, width

---

#### 방향성

세로 모드인지 가로 모드인지, orientation으로 검사

---

### 복잡한 미디어 쿼리

#### 논리곱(and) 미디어 쿼리

and를 사용해 미디어 기능 합침

```css
@media screen and (min-width: 400px) and (orientation: landscape) {
  body {
    color: blue;
  }
}
```

#### 논리합(or) 미디어 쿼리

콤마로 분리

```css
@media screen and (min-width: 600px), screen and (orientation: landscape) {
  body {
    color: blue;
  }
}
```

#### 부정(not) 미디어 쿼리

not 연산자 미디어 쿼리의 의미 반대로 적용

```css
@media not all and (orientation: landscape) {
  body {
    color: blue;
  }
}
```
