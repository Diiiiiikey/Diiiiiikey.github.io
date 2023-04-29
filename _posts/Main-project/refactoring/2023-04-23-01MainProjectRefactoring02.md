---
layouts: post
title: "[Project Refactoring]env"
categories: Main-Project
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

client 폴더 바로 안에(package.json과 동일한 위치).env 파일을 만들고 .gitignore에 .env 추가

.env안에

```
REACT_APP_API_URL=서버주소
```

를 입력

다른 페이지에서 console.log(process.env) 를 호출

`REACT_APP_API_URL : 서버주소`

확인

apis-utils-index.js 에 적용

<https://stackoverflow.com/questions/53237293/react-evironment-variables-env-return-undefined>
