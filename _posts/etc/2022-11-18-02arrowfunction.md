---
layouts: post
title:  "화살표함수의 함정"
categories: JS
tag: [mdn]
toc: true
sidebar:
    nav: "docs"
---

- this나 super에 대한 바인딩이 없고, methods 로 사용될 수 없습니다.
- new.target키워드가 없습니다.
- 일반적으로 스코프를 지정할 때 사용하는 call, apply, bind methods를 이용할 수 없습니다.
- 생성자(Constructor)로 사용할 수 없습니다.
- yield를 화살표 함수 내부에서 사용할 수 없습니다.