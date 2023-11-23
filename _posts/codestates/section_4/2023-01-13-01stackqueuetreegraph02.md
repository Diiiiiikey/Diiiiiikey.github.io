---
layouts: post
title: "[Data Structure]Tree"
categories: ALGORITHM
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

## Tree

- 단방향 그래프
- 하나의 뿌리로부터 가지가 사방으로 뻗은 형태
- 데이터가 바로 아래에 있는 하나 이상의 데이터에 한 개의 경로와 하나의 방향으로만 연결된 계층적 자료구조
- 비선형 구조

<html>
    <div style ="text-align:center">
        <img src= "https://user-images.githubusercontent.com/58800295/183905527-63a92add-9606-4e62-ad98-4afdba60dd5b.png" alt="트리" width="700" height="700">
    </div>
</html><br/>

<html>
    <div style ="text-align:center">
        <img src= "https://user-images.githubusercontent.com/58800295/183905662-6299a19e-766c-4611-b125-64745f80dcf9.png" alt="트리" width="700" height="700">
    </div>
</html><br/>

루트(최상위 데이터)부터 여러 개의 데이터를 간선(edge)으로 연결, 각 데이터는 노드(Node), 두 개의 노드가 상하 계층으로 연결되면 부모/자식 관계, 자식이 없는 노드는 리프 노드(Leaf Node)

Tree는 깊이와 높이, 레벨 등을 측정 가능

- 깊이(depth) - 루트로부터 하위 계층의 특정 노드까지, 최상위가 0부터 시작
- 레벨(Level) - 같은 깊이의 노드들, 같은 레벨의 노드를 형제 노드(Sibling Node)
- 높이(Height) - 리프 노드를 기준으로 루트까지, 모 노드는 자식 노드의 가장 높은 height 값에 +1한 값을 높이
- 서브 트리(Sub tree) - 큰 트리의 내부에, 트리 구조를 갖춘 작은 트리를 서브 트리

---

### 이진 트리(binary tree)

자식 노드가 최대 두 개인 노드들로 구성된 트리

왼쪽 자식 노드와 오른쪽 자식 노드

자료의 삽입, 삭제 방법에 따라 정 이진 트리(Full binary tree), 완전 이진 트리(Complete binary tree), 포화 이진 트리(Perfect binary tree)로 나뉨

<html>
    <div style ="text-align:center">
        <img src= "https://user-images.githubusercontent.com/58800295/183912754-d9b3f3af-7285-4219-9181-ef33ecc6564d.png" alt="이진트리" width="700" height="700">
    </div>
</html><br/>

- 정 이진 트리(Full binary tree) - 각 노드가 0개 혹은 2개의 자식 노드
- 포화 이진 트리(Perfect binary tree) - 정 이진 트리이면서 완전 이진 트리. 모든 리프 노드의 레벨이 동일, 모든 레벨이 가득 채워져 있는 트리
- 완전 이진 트리(Complete binary tree) - 마지막 레벨을 제외한 모든 노드가 가득 참, 마지막 레벨의 노드는 전부 차 있지 않아도 되지만 왼쪽은 참
- 이진 탐색 트리와 이진 힙 구현에 사용, 효율적인 검색과 정렬을 위해 사용

---

### 이진 탐색 트리(Binary Search Tree)

이진 탐색(binary search)과 연결 리스트(linked list)를 결합한 이진트리

이진 탐색의 효율적인 탐색 능력 유지, 빈번한 자료 입력 및 삭제 가능

- 각 노드에 중복되지 않는 키(Key) 존재
- 루트노드의 왼쪽 서브 트리는 해당 노드의 키보다 작은 키를 갖는 노드들
- 루트노드의 오른쪽 서브 트리는 해당 노드의 키보다 큰 키를 갖는 노드들
- 좌우 서브트리도 모두 이진 탐색 트리

모든 왼쪽 자식의 값이 루트나 부모보다 작고, 모든 오른쪽 자식의 값이 루트나 부모보다 큰 값

<html>
    <div style ="text-align:center">
        <img src= "https://user-images.githubusercontent.com/58800295/183913183-8b8d6d2a-d36c-47c9-980b-904d0dcb6a56.png" alt="이진탐색트리" width="700" height="700">
    </div>
</html><br/>

균형 잡힌 트리가 아닐 때, 입력되는 값의 순서에 따라 한쪽으로 노드들이 몰리게 될 수 있음

이진 탐색 트리의 연산은 트리의 높이가 h(height)라면 o(h)의 복잡도

1. 루트 노드의 키와 찾고자 하는 값 비교. 찾고자 하는 값이라면 탐색 종료.
2. 찾고자 하는 값이 루트 노드의 키보다 작다면 왼쪽 서브 트리 탐색.
3. 찾고자 하는 값이 루트 노드의 키보다 크다면 오른쪽 서브 트리 탐색.

트리 안에 찾고자 하는 값이 없더라도 최대 h번의 연산 및 탐색이 진행

---

### 트리 순회

특정 목적을 위해 트리의 모든 노드를 한 번씩 방문하는 것

전위 순회, 중위 순회, 후위 순회

#### 전위 순회(preorder traverse)

루트에서 시작해 왼쪽의 노드 탐색, 왼쪽의 노드 탐색이 끝나면 오른쪽 노드 탐색, 부모 노드를 제일 먼저 방문, 주로 부모 노드가 먼저 생성되어야 하는 트리를 복사할 때 사용

#### 중위 순회(inorder traverse)

루트를 가운데에 두고 순회, 왼쪽 끝에 있는 노드부터 시작, 루트를 기준으로 왼쪽에 있는 노드 탐색, 루트를 거쳐 오른쪽에 있는 노드로 이동, 부모 노드를 서브 트리의 방문 중간에 방문, 이진 탐색 트리의 오름차순으로 값을 가져올 때

#### 후위 순회(postorder traverse)

루트를 마지막에 순회, 왼쪽 끝에 있는 노드부터 시작, 루트를 거치지 않고 오른쪽으로 이동 후 탐색, 마지막에 루트를 방문, 트리를 삭제할 때 사용(자식 노드가 먼저 삭제되어야 상위 노드를 삭제할 수 있기 때문)

순회 방식의 분리는 트리 구조를 유지보수하거나 특정 목적을 위해서도 순회 방법에 대한 정의는 필수적으로 필요

#### 레벨순회(levelorder traversal; BFS)

루트 노드를 먼저 탐색하고, 그 다음 레벨의 노드를 탐색하는 방식
