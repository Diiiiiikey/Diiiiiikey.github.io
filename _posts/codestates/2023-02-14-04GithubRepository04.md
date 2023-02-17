---
layouts: post
title: "[Git]Git branch"
categories: Project
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

## Git branch

기존 개발중인 메인 개발 코드를 그대로 복사하여 새로운 기능 개발을 메인 개발 코드를 건드리지 않고 할 수 있는 버전 관리 기법

main 브랜치에서만 작업을 하다가 새로운 기능 개발을 위해 feature 브랜치를 새로 생성

main 브랜치에서의 작업은 유지하고 새로운 feature 브랜치에서 자유롭게 코드를 추가 및 삭제 가능

---

### 브랜치 생성하기 / 변경하기 (git switch)

---

새로운 브랜치로 Git이 바라보는 곳, HEAD를 변경하는 작업을 switch

생성(create) -c 를 붙여줘야 하고, 기존에 있는 브랜치로 옮길 때는 붙이지 않아도 됨

```
feature라는 브랜치를 새로 생성
git switch -c feature

# 같은 의미
git checkout -b feature



# 기존에 있던 main 브랜치로 HEAD를 변경
git switch main
```

<html>
    <div style ="text-align:center">
        <img src= "https://s3.ap-northeast-2.amazonaws.com/urclass-images/3evgh0HEjV22WOP8itQPW-1660886068826.jpeg" alt="branch" width="600" height="600">
    </div>
</html><br/>

---

### 브랜치 합치기 (git merge)

---

```
# 기능 개발
git commit -m "기능1 세부"
git commit -m "기능1 완료"


# 머지를 위해 main 브랜치로 전환
git switch main

# main 브랜치로 feat/todo 브랜치를 병합
git merge feat/todo
```

Github의 pull request 기능을 이용하여 변경 내역을 확인 후 머지하는 경우가 더 많다.

feature 브랜치를 push하여 pull request를 요청하는 것을 권장

```
# 기능 개발
git commit -m "기능1 세부"
git commit -m "기능1 완료"


# Github 리포지토리로 푸시
git push origin feat/todo

# Github에서 Pull Request
```

### 브랜치 삭제하기 (git branch -d)

---

머지된 feature 브랜치는 이미 dev 브랜치에 기록이 완벽하게 남아있기 때문에 굳이 남겨둘 이유가 없어 삭제 권장

원격 리포지토리에서 pull request가 성공적으로 마무리되면 삭제

<html>
    <div style ="text-align:center">
        <img src= "https://s3.ap-northeast-2.amazonaws.com/urclass-images/bpZza0w1nL9YScYSorbZN-1660921491146.png" alt="branch 삭제" width="600" height="600">
    </div>
</html><br/>

```
git branch -d feat/todo

# 브랜치가 합져지지 않으면 삭제가 못하도록 설정되어 있다. 중간에 삭제를 하고 싶은 경우에는

git branch -D feat/todo
```
