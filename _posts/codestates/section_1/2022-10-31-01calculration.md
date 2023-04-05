---
layouts: post
title: "[MOCKUP]계산기"
categories: CSS
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

```css
/* 리셋 */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  border: none;
}

/* 버튼 포인터 */
button {
  cursor: pointer;
}

/* 버튼 호버 투명도 0.5 */
button:hover {
  opacity: 0.5;
}

/* 100vh는 브라우저 화면의 높이만큼의 길이
align-items: center;로 정렬을해도 100vh를 넣지 않으면
상하 정렬이 되지 않음 */
body {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

/* box-shadow: 수평거리, 수직거리, 흐림정도, 확산정도, 색상
바탕의 색을 결정함, 높이와 폭을 결정함 */
section {
  border-radius: 10px;
  width: 400px;
  height: 600px;
  background-color: #504f51;
  box-shadow: 10px 10px 20px 0px #787778;
}

/* 평범한 화살표 커서 */
.colors_box {
  cursor: default;
}
/* 버튼 자체의 높이로 헤더의 높이가 정해졌다 25px */
.colors {
  margin: 5px;
  width: 15px;
  height: 15px;
  border-radius: 50%;
}

.colors:first-child {
  background-color: #ed5951;
}

.colors:nth-child(2) {
  background-color: #f8b439;
}

.colors:last-child {
  background-color: #50be3f;
}

/* 메인의 높이는 100px */
main {
  width: 100%;
  height: 100px;
  padding: 15px;
}

#number_output:hover {
  cursor: default;
}

/* 아웃풋의 너비는 섹션의 너비 400px에 메인의 너비 100%에 패딩 15px을 뺀 370px
높이는 메인의 높이 100px에 패딩 15px을 뺀 70px */
#number_output {
  display: flex;
  justify-content: right;
  width: 100%;
  height: 100%;
  font-size: 55px;
  color: #fff;
}

/* 버튼박스의 높이는 섹션의 높이 - 헤더와 메인의 높이 */
.btns_box {
  width: 100%;
  height: calc(600px - 125px);
}

/* 버튼박스 바로 아래있는 div 가로줄, 혹시 모르니 세로 센터 정렬,
높이는 20%, 5줄이기 때문 */
.btns_box > div {
  display: flex;
  align-items: center;
  height: 20%;
}

/* AC는 다른 칸보다 3배 큼 flex-grow: 3 */
#AC {
  flex: 3;
}

/* 버튼박스 안에 있는 버튼들, 4개이기 때문에 너비는 25%, 높이는 버튼 박스의 475px의 가로줄 20%로 95px의 100%
섹션 위에 다른 색상 입힘 */
.btns_box button {
  width: 25%;
  height: 100%;
  border-top: 1px solid #000;
  background-color: #6f6f6f;
  font-size: 40px;
  color: #fff;
}

.btns_box button:not(button:first-child) {
  border-left: 1px solid #000;
}

.line_first button:first-child {
  background-color: #909090;
}

button.orange {
  background-color: #f8b439;
}

.line_fifth button:first-child {
  border-bottom-left-radius: 10px;
  flex: 2;
}

.line_fifth button:last-child {
  border-bottom-right-radius: 10px;
}

/* 버튼을 누를 때 활성화됨
transform: scale(1, 1) 가로와 세로의 비율 1, 1이면 현재크기와 같음.
translate(0, 2px) 가로, 세로만큼 이동 */
button:active {
  transform: scale(1, 1) translate(0, 2px);
}
```
