---
layouts: post
title: "[Project Management] Git"
categories: Main-Project
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

README.md

프로젝트 이름
프로젝트 핵심 기능 소개
팀원 소개

.gitignore
git으로 관리하지 않는 파일 모음

secret token, 다른 동료와 공유할 필요가 없는 설정 파일 git이 이를 파악하지 않고 push되지 않음

어떤 git flow를 사용할 것인가

Coz Git flow

## Git branch

### Git 설정

---

버전 히스토리를 식별할 때 사용할 이름

```
git config --global user.name "[firstname lastname]"
```

---

각 기록과 연결할 이메일 주소

```
git config --global user.email “[valid-email]”
```

---

### 도움말

---

모든 명령어

```
git help -all
```

---

특정 command에서 사용할 수 있는 모든 옵션

```
git [command] -help
```

---

### 세팅 및 초기화 - 레포지토리 초가화, 레포지토리를 클론

---

Git 저장소 생성

```
git init
```

---

URL을 통해 리모트 레포지토리를 로컬 레포지토리에 복제

```
git clone [url]
```

---

### Stage & Commit

---

수정된 파일 확인

```
git status
```

---

파일 추가(스테이지)

```
git add [file]
```

---

언스테이징

```
git reset [file]
```

---

스테이지되지 않은 변경 사항

```
git diff
```

---

스테이징, 커밋하지 않은 변경 사항

```
git diff --staged
```

---

스테이지된 컨텐츠를 메시지와 함께 커밋

```
git commit -m “[descriptive message]”
```

---

### Branch & Merge

작업 내역을 브랜치로 분리, 컨텍스트, 변경, 통합 가능

---

브랜치 목록. \* 표시로 현재 작업중인 브랜치 확인

```
git branch
```

---

현재 커밋에서 새로운 브랜치 생성

```
git branch [branch-name]
```

---

다른 브랜치 전환

```
git switch [branch-name]
git checkout [branch-name]
```

---

새로은 브랜치 생성, 해당 브랜치로 전환

```
git switch -c [branch-name]
git checkout -b [branch-name]
```

---

현재 브랜치에 특정 브랜치의 히스토리 병합

```
git merge [branch-name]
```

---

현재 브랜치의 모든 커밋 히스토리

```
git log
```

---

### 비교 및 검사

로그 및 변경 사항 검사

---

브랜치B에 없는 브랜치A의 모든 커밋 히스토리

```
git log branchB..branchA
```

해당 파일의 변경 사항이 담긴 모든 커밋 표시(파일 이름 변경도 표시)

```
git log --follow [file]
```

브랜치A에 있지만 브랜치B에 없는 것의 변경 내용(diff) 표시(branch간 상태 비교)

```
git diff branchB...branchA
```

---

### 공유 및 업데이트

특정 레포지토리의 업데이트 사항을 검색, 로컬 레포지토 업데이트 가능

---

url을 통해 특정 리모트 레포지토리를 별칭으로 추가

```
git remote add [alias] [url]
```

---

별칭으로 추가한 리모트 레포지토리에 있는 모든 브랜치 및 데이터를 로컬

```
git fetch [alias]
```

---

리모트 브랜치를 현재 작업중인 브랜치와 병합하여 최신 상태로

```
git merge [alias]/[branch]
```

---

로컬 브랜치의 커밋을 리모트 브랜치로

```
git push [alias] [branch]
```

---

리모트 레포지토리의 정보를 가져와 자동으로 로컬 브랜치에 병합

```
git pull
```

---

### 히스토리 수정

브랜치 또는 커밋 수정, 커밋 히스토리 삭제

---

특정 브랜치의 분기 이후 커밋을 현재 작업중인 브랜치

```
git rebase [branch]
```

---

특정 커밋 전으로 돌아가며 스테이지된 변경 사항 모두 삭제

```
git reset --hard [commitish]
```

---

### 임시 저장

---

수정하거나 스테이지된 변경사항을 스택에 임시 저장하고 현재 작업 내역에서 삭제

```
git stash
```

---

스택에 임시 저장된 변경사항의 목록

```
git stash list
```

---

스택에 임시 저장된 변경사항을 다시 현재 작업 내역에 적용

```
git stash apply
```

---

스택에 임시 저장된 변경사항을 다시 현재 작업 내역에 적용하고 스택에서 삭제

```
git stash pop
```

---

스택에 임시 저장된 변경사항 삭제

```
git stash drop
```

---
