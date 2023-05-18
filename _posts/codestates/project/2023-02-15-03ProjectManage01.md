---
layouts: post
title: "[SRS]프로젝트 개요"
categories: PROJECT
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

## SRS(Software requirements specification)

- 소프트웨어가 무엇을 할 것이며 어떻게 작동할 것으로 예상되는지 설명하는 문서
- 제품이 모든 이해 관계자(비즈니스, 사용자)의 요구를 충족시키는데 필요한 기능 설명
- 소프트웨어(제품)를 기획/분석, 설계, 구현, 시험 하는데 있어 필요한 종합 설계도

### SRS가 중요한 이유

---

- 과업 발생
- 사업자 선정 및 계약
- 기획 / 분석
- 설계
- 구현
- 시험
- 서비스 오픈
- 유지보수

---

### 개발 프로젝트 구분

---

- 솔루션 - 기업에서 개발한 제품
- SI(System Integration) - 시스템 구축
- SM(System Managemnet) - 시스템 운영 및 유지보수

---

### SRS의 구성

---

1. 소개

   1. 목적 (Purpose)

      이 문서에 요구사항이 명시되어 있는 제품 또는 애플리케이션을 설명한다. 이 SRS가 전체 시스템 중 일부에만 관련된 것이라면 그 부분 또는 하위시스템을 설명한다.

   2. 문서 규칙 (Document Convention)

      텍스트 스타일, 하이라이트 또는 주석과 같은 모든 표준 또는 표기규칙을 설명한다.

   3. 독자대상과 읽는 방법 (Intend Audience and Reading Suggestion)

      SRS가 대상으로 하고있는 다양한 독자계층을 나열한다. SRS의 나머지 부분과, SRS가 조직되어 있는 방법을 설명하고, 각각의 독자 계층에 대해 가장 적합한 읽기 순서를 설명한다.

   4. 프로젝트 범위 (Project Scope)

      설명되고 있는 소프트웨어와 그 목적에 대해 간단하게 설명한다.

   5. 참조 (Reference)

      이 SRS가 참조하고 있는 모든 문서 또는 다른 리소스를 나열하며, 가능한 경우에는 하이퍼링크도 포함시킨다.

2. 전체 설명 (Overall Description)

   1. 제품조망 (Product Perspective)

      제품의 구성과 유래를 설명한다. 제품이 확장되는 제품군의 다음 구성제품인지, 완성된 시스템의 다음 버전인지, 기존 애플리케이션을 대체하는 것인지, 완전히 새로운 제품인지를 설명한다.

   2. 제품 기능 (Project Feature)

      제품이 가지고있는 주요기능 또는 제품이 수행하는 중요한 기능을 나열한다. 요구사항의 주요 그룹과 그 그룹이 연결되어 있는 방법을 설명하는 최상위 데이터 플로우 다이어그램, 유스케이스 다이어그램, 클래스 다이어그램 등이 도움이 된다.

   3. 사용자 계층과 특징 (User Classes and Characteristic)

      이 제품을 사용할 것으로 예상되는 사용자계층을 파악하고 그들의 특징을 설명한다.

   4. 운영 환경 (Operation Environment)

      하드웨어 플랫폼, 운영체계와 버전, 사용자, 서버와 데이터베이스의 지리적 위치 등과 같은 소프트웨어가 동작되는 환경을 설명한다. 시스템이 아무런 문제없이 연동해야 하는 다른 소프트웨어 컴포넌트 또는 애플리케이션을 나열한다.

   5. 설계 및 구현 제약사항 (Design and Implementation constraint)

      - 개발자가 선택할 수 있는 사항을 제약하는 모든 요소와 각 제약조건의 이유를 설명한다. 제약 조건은 다음과 같다.
      - 반드시 사용하거나 피해야 하는 기술, 툴, 프로그래밍 언어와 인터페이스.
      - 사용될 웹 브라우저의 유형과 버전과 같이 제품의 운영환경으로 인한 제약.
      - 필요한 개발 규칙 또는 표준(예를 들면 고객의 조직이 소프트웨어를 유지보수 할 예정이라면, 그 조직은 하청업체가 따라야 하는 설계 표기법과 코딩 표준을 명시 할 수 있다.)
      - 이전 제품과의 호환성.
      - 비즈니스 규칙에 따른 제약.
      - 메모리 또는 프로세스의 제약, 크기, 무게, 비용과 같은 하드웨어의 제약.
      - 기존 제품을 개선하는 경우에 따라야 하는 기존 사용자 인터페이스 규칙.
      - XML과 같은 표준 데이터 교환 형식.

   6. 사용자 문서 (User Documentation)

      소프트웨어와 함께 제공할 사용자 문서를 나열한다. 사용자 문서로는 사용자 메뉴얼, 온라인 도움말, 교재 등이 있으며 따라야 하는 문서 전달 형식, 표준 또는 툴이 있다면 그것들을 설명한다.

   7. 가정과 종속관계 (Assumptions and Dependencies)

      가정이 잘못되거나 이것을 공유하지 않는다면 문제가 발생될 수 있기 때문에 어떤 가정은 프로젝트 위험으로 간주된다. 프로젝트가 통제할 수 없는 외부 요소에 어느정도 종속되는지 또한 설명해야 한다.

3. 시스템 특징 (System Feature)

   1. 시스템 특징

      1. 설명과 우선순위 (Description and Priority)

         기능에 대해 간단하게 설명하고 그것이 높은 우선순위인지 낮은 우선순위인지를 나타낸다. 우선순위는 프로젝트 중에 변할 수 있는 동적인 것으로, 요구사항관리 툴을 사용한다면 요구사항 특성의 우선순위를 정의한다.

      2. 자극/응답 순서 (Stimulus / Response Sequence)

         입력 자극(사용자 행동, 외부 장비의 신호 또는 다른 자극)의 순서와 이 기능에 대한 동작을 정의하는 시스템 반응을 나열한다.

      3. 기능 요구사항 (Functional Requirement)

         이 기능과 관련된 상세한 기능 요구사항을 항목으로 나열한다. 이것들은 사용자가 기능의 서비스를 수행하기 위해 또는 유스케이스를 수행하기 위해 사용하는 소프트웨어의 기능들이다.

4. 외부 인터페이스 요구사항 (External Interface Requirement)

   1. 사용자 인터페이스 (User Interface)

      - 시스템이 요구하는 각각의 사용자 인터페이스와 논리적인 특징을 설명한다. 따라야 할 GUI 표준 또는 제품 스타일 가이드에 대한 참조.
      - 폰트, 아이콘, 버튼 레이블, 이미지, 색상 체계, 필드탭 순서, 공통으로 사용되는 컨트롤 등에 대한 표준.
      - 화면 레이아웃 또는 해상도 제약 조건.
      - 도움말 버튼과 같이 모든 화면에 나타나는 표준 버튼, 기능 또는 탐색 링크.
      - 단축키.
      - 메시지 표시 규칙.
      - 소프트웨어 번역을 원활하게 하는 레이아웃 표준.
      - 시각장애자를 위한 기능.
      - 사용자 인터페이스 설계 상세 내용은 SRS가 아닌 별도의 사용자
      - 인터페이스 명세에 문서로 정리한다.

   2. 하드웨어 인터페이스 (Hardware Interface)

      시스템의 소프트웨어와 하드웨어 컴포넌트간의 모든 인터페이스의 특징을 설명한다. 설명에는 지원되는 장비 유형, 소프트웨어와 하드웨어간의 데이터와 컨트롤 연동, 사용될 통신 프로토콜 등이 포함된다.

   3. 소프트웨어 인터페이스 (Software Interface)

      이 제품과 다른 소프트웨어 컴포넌트(데이터베이스, 운영체제, 툴, 라이브러리, 통합 상업용 컴포넌트)간의 연결을 설명한다. 소프트웨어 컴포넌트 간에 교환되는 메시지, 데이터와 컨트롤 항목을 설명한다.

   4. 통신 인터페이스 (Communication Interface)

      이메일, 웹 브라우저, 네트워크 통신 프로토콜, 전자 문서와 같이 제품이 사용할 모든 통신 기능에 대한 요구사항을 설명한다. 관련된 모든 메시지 형태를 정의하고 통신 보안 또는 암호화 문제, 데이터전송률과 동기화 메커니즘을 명시한다.

5. 기능 이외의 다른 요구사항 (Other Nonfunctional Requirements)

   1. 성능 요구사항 (Performance Requirement)

      다양한 시스템 운영에 대한 특정 성능 요구사항을 설명한다. 개발자들이 적합한 설계를 선택할 수 있게 만든 논리를 설명한다.

   2. 안전 요구사항 (Safety Requirement)

      반드시 방지해야 하는 잠재적으로 위험한 행동 뿐만 아니라 반드시 취해야 할 모든 안전장치 또는 행동을 정의한다. 제품이 따라야 하는 보안인증, 정책 또는 규제를 정의한다.

   3. 보안 요구사항 (Security Requirement)

      제품에 대한 접속과 제품사용에 영향을 미치는 보안, 무결성 또는 사생활 문제, 제품이 사용하거나 만드는 데이터 보호를 모두 명시한다.

   4. 소프트웨어 품질 특성 (Software Quality Attribute)

      고객 또는 개발자에게 중요한 모든 별도의 품질 특성을 설명한다. 이런 특성들은 명확하고 계량적이며 확인이 가능해야 한다.

6. 다른 요구사항 (Other Requirement)

SRS의 다른 부분에서는 다루지 않는 모든 요구사항을 정의한다.