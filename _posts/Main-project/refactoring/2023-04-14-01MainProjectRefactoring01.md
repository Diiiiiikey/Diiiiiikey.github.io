---
layouts: post
title: "[Project Refactoring]배포"
categories: Main-Project
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

우리 팀의 프로젝트는 리팩토링이 너무나도 필요하다. 모든 부분에서 필요하다고 생각이 들기 때문에 기존의 프로젝트를 건들지 않고 fork로 새로운 repository로 리팩토링을 진행할 것이며 또한 https를 적용하기 위해 서버와 클라이언트 모두 새롭게 배포를 한다.

ec2 배포 참고

<https://hojung-testbench.tistory.com/entry/AWS-EC2-%EC%9D%B8%EC%8A%A4%ED%84%B4%EC%8A%A4%EB%A5%BC-%EC%9D%B4%EC%9A%A9%ED%95%9C-%EB%B0%B0%ED%8F%AC-NextJS-Express>

<https://kang-james.tistory.com/entry/%EB%B0%B0%ED%8F%AC-AWS%EB%A5%BC-%ED%86%B5%ED%95%9C-%EB%B0%B0%ED%8F%AC-%EB%B0%A9%EB%B2%95-%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0EC2-%EC%84%9C%EB%B2%84-%EC%8B%A4%ED%96%89>

ec2 배포 중 인스턴스에 연결 - SSH 클라이언트 - chmod 400 설정 window에서

<https://zagg2732.tistory.com/m/50>

우분투로 다시 인스턴스 생성하자

<https://programming119.tistory.com/203>

포기 라이트세일로 시도

<https://inpa.tistory.com/entry/MobaXterm-%F0%9F%92%BD-%EB%AA%A8%EB%B0%94%EC%97%91%EC%8A%A4%ED%85%80-%EC%84%A4%EC%B9%98-%ED%95%9C%EA%B8%80%ED%99%94-SSH-%EC%A0%91%EC%86%8D-%EB%B0%A9%EB%B2%95-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC>

라이트세일도 못해먹겠다..

4월 20일

다시 ec2로 도전

<https://kang-james.tistory.com/entry/%EB%B0%B0%ED%8F%AC-AWS%EB%A5%BC-%ED%86%B5%ED%95%9C-%EB%B0%B0%ED%8F%AC-%EB%B0%A9%EB%B2%95-%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0EC2-%EC%84%9C%EB%B2%84-%EC%8B%A4%ED%96%89>

에러해결

<https://www.inflearn.com/questions/236464/%EC%97%90%EB%9F%AC-o-s-b-d-loggingfailureanalysisreporter>

빌드하고 java jar 과정에서 application.yml 때문에 오류가 발생

라이트세일로 다시 시도

---

내가 할 수 있는 영역이 아니었다. 백엔드의 한분에게 요청했고

WebConfig.java

```
.allowedOrigins("http://localhost:3000",
"http://milkbubbletea.s3-website.ap-northeast-2.amazonaws.com/",
"http://milkbubbleteafork.s3-website.ap-northeast-2.amazonaws.com")
```

로 수정을 해서
총 세 개의 도메인이 cors 혀용되었다.
