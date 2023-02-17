---
layouts: post
title: "[Github]Github 리포지토리"
categories: Project
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

### Github 리포지토리에 꼭 필요한 파일

---

- README.md

오픈소스 프로젝트에 들어가서 바로 확인 가능한 정보

대체로 어떻게 하면 해당 오픈소스를 활용할 수 있는지에 대한 상세한 정보

`프로젝트 이름, 프로젝트 핵심 기능 소개, 팀원 소개` 를 포함

- .gitignore

gitignore dotfile은 git으로 관리하지 않는 파일 모음

개인이 따로 관리해야 하는 중요한 secret token, 동료와 공유할 필요가 없는 설정 파일, 공유할 필요 없는 파일

git이 이를 파악하지 않고, push 할 때도 github 리포지토리에 push되지 않음

- LICENSE

해당 코드의 라이센스 표기

깃허브에 공개된 리포지토리도 라이센스에 따라서 사용 불가능할 수 있으니 사용할 때 라이센스 확인 필요

회사에서 사용하는 코드는 private으로 관리하고, 외부에 공개하지 않아 라이센스 정보를 따로 표기 안함. 하지만 회사에서 작성하는 코드가 public으로 공개된다면, LICENSE를 명확하게 표기

<https://www.bloter.net/newsView/blt201410100005>

---

### 프로젝트 관리에 활용할 수 있는 Github 기능

---

- Issue

프로젝트에 새로운 기능을 제안, 버그를 찾아 제보 등 프로젝트의 이슈

Pre-Project에서는 Issue를 하나의 칸반 티켓처럼 사용

- Milestone

이정표 역할, 태스크 카드(Issue) 그룹화에 사용

Milestone에 연결된 태스크 카드(Issue)가 종료되면 Milestone마다 진행 상황 업데이트

연관된 이슈의 추적과 진행 상황을 한눈에 파악

Pre-Project에서는 Bare Minimum, Advanced Challenge, Nightmare를 표시

- Pull Request

작업한 내용을 중요 git branch에 합칠 수 있는지 확인하는 요청

Github에서는 Pull Request에서 커밋한 코드를 따로 선택하여 해당 부분에 코멘트 가능

Pull Request 과정에 익숙해지는 것이 중요

- Project

업무 관리를 해줄 수 있게 돕는 새로운 기능

Pre-Project에서는 이 Project 기능을 이용하여 칸반 보드를 생성하고, 칸반으로 Pre-Project의 업무 흐름을 관리
