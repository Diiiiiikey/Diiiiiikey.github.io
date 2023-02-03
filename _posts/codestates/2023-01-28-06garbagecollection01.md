---
layouts: post
title:  "가비지 컬렉션"
categories: computer
tag: [codestates]
toc: true
sidebar:
    nav: "docs"
---

## 가비지 컬렉션

프로그램에서 더 이상 사용하지 않는 메모리를 자동으로 정리하는 것

자바, C#, 자바스크립트 등

JavaScript는 고수준 언어로서, 객체가 생성되었을 때 자동으로 메모리를 할당하고 필요하지 않다면 자동으로 해제하는 가비지 컬렉션이 내장

---

#### 고수준 언어와 저수준 언어
---

프로그래밍 언어가 인간에 친화적인지, 기계에 친화적인지에 따라 갈림.

저수준 언어
- 기계 친화적인 언어
- 레지스터 및 메모리와 직접 상호 작용
- 전반적으로 빠르게 실행되는 응용 프로그램을 빌드하는데 사용
- 컴파일러나 인터프리터가 필요하지 않으므로 고수준 언어보다 빠른 편

고수준 언어
- 인간 친화적인 언어
- 간이 이해하기 쉽고 다양한 작업을 수행하는 프로그램을 개발
- 컴파일러 또는 인터프리터를 사용하여 컴퓨터가 읽을 수 있는 기계어 코드로 변환 필요
- 하드웨어와 직접 상호 작용하지 않음

---

### 메모리 생존주기
---

그 어떤 프로그래밍 언어에 관계 없이 비슷

1. 필요할 때 개발자가 할당
2. 할당된 메모리 사용(Read and Write)
3. 메모리가 더이상 필요하지 않으면 해제

2번 은 모든 언어에서 명시적으로 사용(JS에서 변수 선언과 할당)

1번, 3번은 저수준 언어에서 명시적, 고수준 언어에서 암묵적으로 작동(JS에서 직접 제어하지 않음)

---

#### 메모리 할당
---

JS는 값을 선언 시, 자동으로 메모리 할당

변수를 선언하고 할당할 때 메모리 크기를 고려하지 않음

---

#### 할당된 메모리 사용 (값 사용)
---

할당된 메모리를 읽고 쓰는 것

속성의 값을 읽고 쓰거나, 함수 호출 시에 함수에 인수를 전달하여 수행하는 방식

---

#### 메모리 해제
---

메모리가 더이상 필요없다면 해제를 해야 앱 성능을 저하시키지 않음

저수준 언어는 개발자가 직접 결정, 해제. 따라서, 개발자의 제어 정도가 높음

고수준 언어는 가비키 컬렉션에 의해 수행. 하지만 언어 스스로 메모리가 여전히 필요한가 판단은 비결정적 영역. 따라서, 제한적인 해결책을 구현

---

### 대표적인 가비지 컬렉션의 방법
---

1. 레퍼런스 카운팅
2. 트레이싱

이 두 가지 알고리즘은 참조라는 개념을 의존하고 있음

---

#### 참조(reference)

메모리 관리 관점에서, 어떤 객체가 다른 객체에 접근할 수 있다면 다른 객체를 참조한다고 함

JS 객체는 자신의 프로토타입(prototype)에 대해 암묵적인 참조를 갖고 있고, 자신의 속성(property) 값에 대한 명시적 참조도 가지고 있음

객체 참조는 광의적 개념으로 함수 스코프(function scope)나 글로벌 렉시컬 스코프(global lexical scope)까지도 포함

---

##### 렉시컬 스코핑(lexical scoping)
---

변수 이름이 중첩된 함수에서 해석되는 방식을 정의하는 것, 안쪽의 함수는 부모 함수가 값을 반환한 다음에도 부모 함수의 스코프를 포함

---

### 레퍼런스 카운팅(참조 횟수 계산)
---

한 객체를 참조하는 변수의 수를 추적하는 방법, 가장 단순한 형태의 알고리즘

객체를 참조하는 변수는 처음에는 특정 메모리에 대해 레퍼런스가 하나뿐이지만, 변수의 레퍼런스가 복사될 때마다 레퍼런스 카운트가 늘어남

변수의 값의 바뀌거나, 변수 스코프를 벗어나면 레퍼런스 카운트 감소

0이 되면, 객체와 관련된 메모리를 비울 수 있음

but, 순환 참조로 인한 문제가 생길 가능성이 높음

```js
function reference() {
  var obj1 = {}; 
  var obj2 = {}; 
  obj1.p = obj2; 
  obj2.p = obj1; 
}
reference();
```
서로가 서로를 무한으로 참조, but 스코프를 벗어나면 쓸모 없음, 둘 다 가비시 컬렉션 불가

---

### 트레이싱
---

한 객체에 flag를 두고, 가비지 컬렉션 사이클마다 flag에 표시 후 삭제하는 mark and sweep 방법

객체에 in-use flag를 두고, 사이클마다 메모리 관리자가 모든 객체를 추적해서 사용 중인지 아닌지 mark, 그 후 표시되지 않은 객체를 삭제(sweep)하는 단계를 통해 메모리를 해제

대부분의 가비지 컬렉션이 mark and sweep 알고리즘

mark and sweep 알고리즘은 해당 객체에 닿을 수 있는지 (reachable)을 판단

1. 루트(Roots) 
   - 일반적으로 코드에서 참조되는 전역 변수.
   - 가비지컬렉터는 모든 루트의 완전한 목록을 만들어냄.
   - e.g. JS에서 루트로 동작할 수 있는 전역 변수는 window 객체. Node.js에서 global.
2. 이후 모든 루트와 그 자식들을 검사, 활성화 여부 표시, 루트가 닿을 수 없는 것들은 가비지로 표시
3. 마지막, 가비지 컬렉터는 활성으로 표시되지 않은 모든 메모리를 OS에 반환

참조받지 않는 객체는‘닿을 수 없는 객체기 때문에 가비지 컬렉션을 통해 메모리를 해제할 수 있어 더 나은 방법

---

### 메모리 누수
---

Garbage collected 언어에서 메모리 누수의 주요 원인은 예상치 못한 참조

예상치 못한 참조는 개발자는 더 이상 사용되지 않을 것이라 생각했지만, 어떠한 이유로 활성화 상태인 루트 트리 안에 존재하는 메모리 조각들

코드 상 어딘가에 유지되어 해제되지 못한 변수들

일반적으로
- 우발적으로 생성된 전역변수
- DOM 외부에서의 참조
- 클로저의 잘못된 사용

개발자들만이 해당 메모리 조각을 운영체제로 반환시킬 수 있는지 여부를 명확히 알 수 있기 때문에 해당 부분들을 잘 확인하여 메모리 누수가 일어나는 부분을 막을 줄 알아야 함