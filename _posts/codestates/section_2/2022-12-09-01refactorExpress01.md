---
layouts: post
title: "[WEB SERVER]Refactor Express"
categories: NODE.JS
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

Node.js 환경에서 웹 서버, 또는 API 서버를 제작하기 위해 사용되는 프레임워크 중 하나

Node.js HTTP 모듈로 작성한 서버와 다른 점

- 미들웨어를 추가할 수 있다.
- 라우터를 제공한다.

express 공식 문서<br/>
<https://expressjs.com/ko/starter/hello-world.html>

```js
const express = require("express");
const app = express();
const port = 3000;

app.get("/", (req, res) => {
  res.send("Hello World!");
});

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`);
});
```

응답으로 Hello World!를 보내는 Express 서버 코드

## 기본 라우팅

메서드와 url(/lower, /upper 등)로 분기점을 만드는 것 - 라우팅(Routing)

각 라우트는 하나 이상의 핸들러 함수를 가질 수 있으며, 이러한 함수는 라우트가 일치할 때 실행됩니다.

```js
app.METHOD(PATH, HANDLER);
```

- app은 express의 인스턴스
- METHOD는 HTTP 요청 메소드
- PATH는 서버에서의 경로
- HANDLER는 라우트가 일치할 때 실행되는 함수

애플리케이션의 홈 페이지인 루트 라우트(/)에서 POST 요청에 응답:

```js
app.post("/", function (req, res) {
  res.send("Got a POST request");
});
```

/user 라우트에 대한 PUT 요청에 응답:

```js
app.put("/user", function (req, res) {
  res.send("Got a PUT request at /user");
});
```

/user 라우트에 대한 DELETE 요청에 응답:

```js
app.delete("/user", function (req, res) {
  res.send("Got a DELETE request at /user");
});
```
