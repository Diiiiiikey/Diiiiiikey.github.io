---
layouts: post
title:  "Stack, Queue"
categories: JS
tag: [codestates]
toc: true
sidebar:
    nav: "docs"
---

## 자료구조

여러 데이터의 묶음을 저장하고, 사용하는 방법을 정의

데이터는 분석하고 정리하여 활용해야만 의미를 가짐, 사용하려는 목적에 따라 형태를 구분하고, 분류하여 사용, 데이터를 체계적으로 정리하여 저장하는 것이 활용에 유리

<html>
    <div style ="text-align:center">
        <img src= "https://user-images.githubusercontent.com/58800295/183896064-1f48f0c0-7a67-4d7e-9480-3ab491295752.png" alt="자료구조" width="700" height="700">
    </div>
</html><br/>

### 자료구조 특징

특정한 상황에 놓인 문제를 해결하는 데에 특화

많은 자료구조를 알아두면, 특정 상황에 적합한 자료구조를 적용하여 문제 해결 가능

<https://www.cs.usfca.edu/~galles/visualization/Algorithms.html><br/>
<https://visualgo.net/en>

---

## stack

데이터를 순서대로 쌓는 자료구조

### stack 특징

1. LIFO(Last In First Out)

    ```js
    stack.push(data)
    // 1 <- 2 <- 3 <- 4
    stack.pop()
    // 4, 3, 2, 1
    ```
2. 데이터를 하나씩 넣고, 뺌
3. 하나의 입출력 방향
4. 저장되는 데이터는 유한하고 정적이어야 함

    스택에 저장되는 일반적인 데이터는 로컬 변수(value type 또는 primitive), 포인터 및 함수 프레임
5. 스택의 크기는 제한적

### 대표적 stack 예시 - 브라우저 뒤로 가기, 앞으로 가기

1. 새로운 페이지 접속 시, 현재 페이지를 Prev Stack에 보관
2. 이전 페이지로 돌아갈 때, 현재 페이지를 Next Stack에 보관, Prev Stack에 가장 나중에 보관된 페이지를 가져옴
3. 앞서 방문한 페이지로 이동할 때, Next Stack의 가장 마지막으로 보관된 페이지를 가져옴
4. 마지막으로 현재 페이지를 Prev Stack에 보관

---

## queue

대기행렬

### queue 특징

1. FIFO (First In First Out)

    ```js
    queue.enqueue(data)
    // 1 <- 2 <- 3 <- 4
    queue.dequeue(data)
    // 1, 2, 3, 4
    ```
2. 데이터를 하나씩 넣고, 뺌
3. 입출력 방향이 다름

### 대표적 stack 예시 - 프린터

컴퓨터(출력 버튼) - (임시 기억 장치의) Queue에 하나씩 들어옴 - Queue에 들어온 문서를 순서대로 인쇄

#### 버퍼(buffer)

컴퓨터 장치들 사이에서 데이터를 주고받을 때, 각 장치 사이에 존재하는 속도의 차이나 시간 차이를 극복하기 위해 임시 기억 장치의 자료구조로 Queue를 사용

규칙적으로 발생한 이벤트를 규칙적으로 처리하기 위해 버퍼(buffer)를 사용

컴퓨터와 프린터의 데이터 통신

1. CPU는 빠르고 프린터는 느림
2. CPU는 빠르게 인쇄에 필요한 데이터를 만들고 인쇄 queue에 저장, 다른 작업 수행
3. 프린터는 Queue에서 데이터를 받아 수행

### 원형 큐 (Circular Queue)

선형 큐의 front와 rear값이 계속 증가하기만 한다는 문제점을 극복한 구조