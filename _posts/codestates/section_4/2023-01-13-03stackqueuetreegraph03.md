---
layouts: post
title: "[Data Structure]Graph"
categories: ALGORITHM
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

## Graph

여러개의 점들이 서로 복잡하게 연결되어 있는 관계를 표현한 자료구조

<html>
    <div style ="text-align:center">
        <img src= "https://user-images.githubusercontent.com/58800295/183922941-bd1dca8e-4cd3-4a80-b4dd-3eaf75596c3c.png" alt="그래프" width="700" height="700">
    </div>
</html><br/>

- 직접적인 관계가 있는 경우 두 점 사이를 이어주는 선
- 간접적인 관계라면 몇 개의 점과 선에 걸쳐 이어짐
- 하나의 점을 정점(vertex), 하나의 선은 간선(edge), 간선에는 양방향 간선, 단방향 간선

### 인접 행렬

간선이 있다면 이 두 정점은 인접하다.

인접 행렬은 서로 다른 정점들이 인접한 상태인지를 표시한 행렬로 2차원 배열의 형태로 나타냄

이어져 있다면 1(true), 이어져 있지 않다면 0(false)

가중치 그래프라면 1 대신 관계에서 의미 있는 값을 저장

내비게이션 예제라면, 거리를 입력

<html>
    <div style ="text-align:center">
        <img src= "https://user-images.githubusercontent.com/58800295/183923500-fa836246-35d7-4a31-90a3-26a4f5376078.png" alt="내비게이션 그래프" width="600" height="600">
    </div>
</html><br/>

- A의 진출차수는 1개 입니다: A —> C
  - [0][2] === 1
- B의 진출차수는 2개 입니다: B —> A, B —> C
  - [1][0] === 1
  - [1][2] === 1
- C의 진출차수는 1개입니다: C —> A

  - [2][0] === 1

- 한 개의 큰 표와 같은 모습을 한 인접 행렬의 정점 확인 시 사용
  - e.g. A에서 B로 진출하는 간선이 있는지 파악하기 위해선 0 번째 줄의 1 번째 열에 어떤 값이 저장되어있는지 바로 확인
- 가장 빠른 경로(shortest path) 탐색 시 사용

#### 인접 리스트

각 정점이 어떤 정점과 인접하는지 리스트의 형태로 표현

<html>
    <div style ="text-align:center">
        <img src= "https://user-images.githubusercontent.com/58800295/183923705-ee09ea5f-d046-4c18-b4c8-e6f20680026b.png" alt="내비게이션 그래프" width="600" height="600">
    </div>
</html><br/>

정점별로 살펴봐야 할 우선 순위를 고려할 때가 있다.

- 메모리를 효율적으로 사용하고 싶을 때
  - 연결 가능한 모든 경우의 수를 저장하기 때문에 상대적으로 메모리 차지

---

### Graph 용어

- 정점(vertex) - 노드(node)라고도 하며, 데이터가 저장되는 그래프의 기본 원소
- 간선(edge) - 정점 간의 관계 나타냄(정점을 이어주는 선)
- 인접 정점(adjacent vertex) - 직접 연결되어 있는 정점
- 가중치 그래프(weighted Graph) - 연결의 강도(추가적인 정보, ex. 서울-부산으로 가는 거리 등)가 얼마나 되는지 적힌 그래프
- 비가중치 그래프(unweighted Graph) - 연결의 강도가 적혀져 있지 않는 그래프
- 무(방)향 그래프(undirected graph) -
- 진입차수(in-degree) / 진출차수(out-degree) - 한 정점에 진입(들어오는 간선)하고 진출(나가는 간선)의 개수
  인접(adjacency) - 두 정점 간에 간선이 직접 이어져 있다면 이 두 정점은 인접
  자기 루프(self loop) - 정점에서 진출하는 간선이 곧바로 자기 자신에게 진입하는 경우 자기 루프를 가졌다 라고 표현. 다른 정점을 거치지 않는다는 것이 특징.
  사이클 (cycle) - 한 정점에서 출발하여 다시 해당 정점으로 돌아갈 수 있다면 사이클.

---

### BFS와 DFS

그래프의 모든 정점 탐색 방법 중 가장 대표적인 두 가지 방법

그래프의 탐색은 하나의 정점에서 시작하여 그래프의 모든 정점들을 한 번씩 방문(탐색)하는 것이 목적

자료를 찾으려면, 하나씩 모두 방문

#### BFS(Breadth-First Search)

너비를 우선적으로 탐색하는 방법

주로 두 정점 사이의 최단 경로를 찾을 때 사용

최악의 경우에는 모든 경로를 다 살펴볼 수도

정점에서 같은 레벨의 정점부터 탐색?

#### DFS(Depth-First Search)

하나의 경로를 끝까지 탐색한 후, 찾는 값이 아니라면 다음 경로로 넘어가 탐색

다음 경로로 넘어가기 전에 해당 경로를 완벽하게 탐색할 때 사용

방향을 정하고 끝까지 탐색?
