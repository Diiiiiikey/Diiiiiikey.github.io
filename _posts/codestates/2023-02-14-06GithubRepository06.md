---
layouts: post
title: "[Git]Git flow"
categories: Project
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

## 브랜칭 전략

브랜치의 종류를 나눠서 관리하는 전략

가장 유명한 브랜칭 전략이 Git flow

<html>
    <div style ="text-align:center">
        <img src= "https://s3.ap-northeast-2.amazonaws.com/urclass-images/4Rbuffv6T2Bs_aYy8MBxn-1660886333969.png" alt="git flow 전략" width="600" height="600">
    </div>
</html><br/>

<html>
    <div style ="text-align:center">
        <img src= "https://s3.ap-northeast-2.amazonaws.com/urclass-images/vEAcD2ryoNSo-6dGo_MIW-1660886461321.jpeg" alt="Coz git flow 전략" width="600" height="600">
    </div>
</html><br/>

---

### main 브랜치

---

사용자에게 언제든 제품으로 출시할 수 있는 브랜치

- 대표적인 기능 완성
- 기획했던 레이아웃, 전체적인 디자인 얼추 완성
- 클라이언트, 서버, 데이터베이스가 공개된 웹에서 정상적으로 통신
- 최소한의 보안
  - 브라우저에서 개발 버전에서 사용하던 secret이나 유저의 비밀번호가 노출되나?
  - 유저의 기밀 정보 조회를 위해 인증 토큰, 세션이 꼭 필요한가?

---

### dev 브랜치

---

개바 중인 브랜치

main 브랜치와 dev 브랜치는 Github 리포지토리에 늘 업데이트

코드 리뷰를 받고 진행

“어떤 코드의 어디를 왜 이렇게 바꿨으면 좋겠다.”라는 코멘트를 Github Pull Request에 남기는 것을 권장

---

### feature 브랜치

---

기능 개발, 리펙토링, 문서 작업, 단순 오류 수정 등 다양한 작업 기록

feature 브랜치 이름과 커밋 메시지의 예시 <https://www.conventionalcommits.org/ko/v1.0.0/>

작은 기능이라도 브랜치를 새로 만들고, 자주 커밋하고, 자주 원격 Github 리포지토리에 push하여 팀원들과 결과를 공유하는 것이 바람직
