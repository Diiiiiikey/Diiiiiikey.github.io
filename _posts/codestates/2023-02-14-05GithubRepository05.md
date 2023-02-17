---
layouts: post
title: "[Git]Git 설정"
categories: Project
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

### 로컬 레포지토리와 연결할 유저 정보를 설정

```
# 버전 히스토리를 식별할 때 사용할 이름 설정
git config --global user.name "[firstname lastname]"

# 각 기록과 연결할 이메일 주소 설정.
git config --global user.email “[valid-email]”
```

---

### 레포지토리 초가화하거나 존재하는 레포지토리 클론

---

```
# 현재 디렉토리를 기준 Git 저장소가 생성
git init

# URL을 통해 리모트 레포지토리를 로컬 레포지토리에 복제
git clone [url]
```

---

### 스테이지 영역을 이용하여 커밋

```
# 수정된 파일을 확인
git status

# 파일을 추가
git add [file]

# 추가한 파일을 언스테이징(add 취소), 변경사항 유지
git reset [file]

# 스테이지되지 않은 변경 사항 확인
git diff

# 스테이지했지만 커밋하지 않은 변경 사항 확인
git diff --staged

# 스테이지된 컨텐츠를 메시지와 함께 커밋
git commit -m “[descriptive message]”
```

---

### 작업 내역을 브랜치로 분리해 컨텍스트 변경, 통합

---

```
# 브랜치 목록, * 표시로 현재 작업중인 브랜치 확인
git branch

# 현재 커밋에서 새로운 브랜치 생성
git branch [branch-name]

# 다른 브랜치로 전환
git switch [branch-name]
git checkout [branch-name]

# 새로은 브랜치 생성, 해당 브랜치로 전환
git switch -c [branch-name]
git checkout -b [branch-name]

# 현재 브랜치에 특정 브랜치의 히스토리 병합
git merge [branch-name]

# 현재 브랜치의 모든 커밋 히스토리
git log
```

---

### 로그 및 변경 사항 검사

---

```
# 브랜치B에 없는 브랜치A의 모든 커밋 히스토리
git log branchB..branchA

# 해당 파일의 변경 사항이 담긴 모든 커밋 표시(파일 이름 변경도 표시)
git log --follow [file]

# 브랜치A에 있지만 브랜치B에 없는 것의 변경 내용(diff) 표시(branch간 상태 비교)
git diff branchB...branchA
```

---

### 특정 레포지토리의 업데이트 사항 검색, 로컬 레포지토리 업데이트할

---

```
# url을 통해 특정 리모트 레포지토리를 별칭으로 추가
git remote add [alias] [url]

# 별칭으로 추가한 리모트 레포지토리에 있는 모든 브랜치 및 데이터를 로컬로 가져옴
git fetch [alias]

# 리모트 브랜치를 현재 작업중인 브랜치와 병합하여 최신 상태로
git merge [alias]/[branch]

# 로컬 브랜치의 커밋을 리모트 브랜치로 전송
git push [alias] [branch]

# 리모트 레포지토리의 정보를 가져와 자동으로 로컬 브랜치에 병합
git pull
```

---

### 브랜치 또는 커밋 수정, 커밋 히스토리 삭제

---

```
# 특정 브랜치의 분기 이후 커밋을 현재 작업중인 브랜치에 반영
git rebase [branch]

# 득정 커밋 전으로 돌아가며 스테이지된 변경 사항 모두 삭제
git reset --hard [commitish]
```

---

### 브랜치를 전환하기 위해 변경되었거나 추적중인 파일을 임시로 저장

---

```
# 수정하거나 스테이지된 변경사항 스택에 임시 저장, 현재 작업 내역에서 삭제
$ git stash

# 스택에 임시 저장된 변경사항의 목록
$ git stash list

# 스택에 임시 저장된 변경사항 다시 현재 작업 내역에 적용
$ git stash apply

# 스택에 임시 저장된 변경사항 다시 현재 작업 내역에 적용, 스택에서 삭제
$ git stash pop

# 스택에 임시 저장된 변경사항 삭제
$ git stash drop
```
