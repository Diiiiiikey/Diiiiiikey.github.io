---
layouts: post
title: "[HTTPS]HTTPS 사설 인증서 발급 및 서버 구현"
categories: NETWORK
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

## 인증서 생성

mkcert으로 로컬 환경(내 컴퓨터)에서 신뢰할 수 있는 인증서 생성

관리자 권한으로 파워셀 열기

Set-ExecutionPolicy AllSigned 입력

<https://chocolatey.org/install> 에서 Now run the following command 복사 후 입력(Chocolatey 다운로드)

<https://github.com/FiloSottile/mkcert> 에서 Windows 따라하기

---

mkcert -key-file key.pem -cert-file cert.pem localhost 127.0.0.1 ::1

localhost, 127.0.0.1(IPv4), ::1(IPv6)에서 사용할 수 있는 인증서 / cert.pem, key.pem 파일 생성

key.pem의 경우 개인 키이므로 git에 커밋하지 않고, 암호처럼 다룸.

---

## .pem

- .pem: X.509 v3 파일의 한 형태
  - PEM (Privacy Enhanced Mail)은 Base64인코딩된 ASCII text file
  - 원래는 secure email에 사용되는 인코딩 포멧이었는데 더이상 email쪽에서는 잘 쓰이지 않고 인증서 또는 키값을 저장하는데 많이 사용됨.
  - `-----BEGIN XXX-----`, `-----END XXX-----` 로 묶여있는 text file을 보면 이 형식으로 인코딩된 것(담고있는 내용이 무엇인지에 따라 XXX 위치에 CERTIFICATE, RSA PRIVATE KEY 등의 키워드가 들어있다)
  - 인증서(Certificate = public key), 비밀키(private key), 인증서 발급 요청을 위해 생성하는 CSR (certificate signing request) 등을 저장하는데 사용.

key - 비대칭 키의 비밀 키<br/>
cert - 인증서

---

## HTTPS 서버 작성

### node.js https 모듈 이용

node server.js 로 서버 실행

```js
const https = require("https");
const fs = require("fs");

https
  .createServer(
    {
      key: fs.readFileSync(__dirname + "/key.pem", "utf-8"),
      cert: fs.readFileSync(__dirname + "/cert.pem", "utf-8"),
    },
    function (req, res) {
      res.write("Congrats! You made https server now :)");
      res.end();
    }
  )
  .listen(3001);
```

---

### express.js 이용

npm install express 부터하고

```js
const https = require("https");
const fs = require("fs");
const express = require("express");

const app = express();

https
  .createServer(
    {
      key: fs.readFileSync(__dirname + "/key.pem", "utf-8"),
      cert: fs.readFileSync(__dirname + "/cert.pem", "utf-8"),
    },
    app.use("/", (req, res) => {
      res.send("Congrats! You made https server now :)");
    })
  )
  .listen(3001);
```

### 서버를 ngrok을 이용해서 HTTPS로 터널링하기

HTTP로 만들어진 서버를 HTTPS 프로토콜로 터널링 해주는 프로그램

외부에서 로컬에 접속 가능하게 하는 터널 프로그램

다운로드 choco install ngrok

npm으로 실행 npm install -g ngrok / ngrok http 8080(server.js에서 정한 post번호)

하지만 안됨

<https://ngrok.com/> 가입하면

나의 Authtoken 값을 받을 수 있음

ngrok authtoken (나의 Authtoken 값) 입력

후 다시 ngrok http 8080 했더니 됨
