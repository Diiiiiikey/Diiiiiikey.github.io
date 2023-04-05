---
layouts: post
title: "[SRS]API 명세서"
categories: PROJECT
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

## REST(Representational State Transfer) API(Application Programming Interface)

웹 애플리케이션은 보통 RESTful한 API를 정의하고 구현

RESTful이란?

리소스는 미디어, DB 데이터 등 모든 자원을 의미

RESTful한 API로써 통신을 할 때 기대하는 결과값에 해당하는 자원들의 일체를 의미

URI(Uniform Resource Identifier)란?

특정 리소스를 식별하는 ‘통합 자원 식별자'

웹 기술에서 사용하는 논리적 또는 물리적 리소스를 식별하는 고유한 문자열 시퀀스

URI는 URL보다 더 큰 범위의 개념

---

### URI 구조

```
scheme:[//[user[:password]@host[:port]][/path][?query][#fragment]
```

- scheme - http 또는 https
- user, password - 데이터가 있는 서버에 접근하기 위해 필요한 ID와 PASSWORD
- host, port - 서버의 호스트와 포트 번호
- path - 서버의 상세 경로
- query - path에 접근하기 위한 추가 정보(파라미터)
- fragment - 메인 리소스 내에 존재하는 서브 리소스에 접근할 때 식별하기 위한 정보

---

### RESTful한 API란 ?

모든 리소스에 대해 고유한 URI를 부여하고 HTTP Method를 적절히 사용하여 리소스를 제어할 수 있는 수단

이때 요청에 대한 응답은 JSON이나 XML과 같은 사전 정의된 형식을 사용하여 일관된 방법으로 주고 받음

---

#### REST 특징

- 서버-클라이언트 구조(Server-Client Architecture)
- 무상태성(Stateless)
- 캐시 가능(Cacheable)
- 일관된 인터페이스(Uniform Interface)
- 자체적인 표현 구조(Self-Descriptiveness)
- 계층 구조(Layered System)

---

### REST 규칙

<html>
    <div style ="text-align:center">
        <img src= "https://s3.ap-northeast-2.amazonaws.com/urclass-images/LjSsDV86UmCYVegzbyH-v-1666589952281.png" alt="REST 규칙" width="700" height="700">
    </div>
</html><br/>

---

### 관계 나타내기

```
http://test.com/groups/1/users
```

- groups, users - 복수 표현. 보통 여러개의 리소스를 갖을 수 있으므로 복수형으로 표시하고 ‘Collection’ 이라고 부름

- 1 - Collection에 포함된 대상 리소스는 단수형 표시, ‘Document’라고 부름

- /groups/1/users - Collection과 Document의 관계를 /를 통해 나타냄. 그룹이라는 Collection 안에 ‘1’ Document를 나타내고, 해당 Document가 갖고 있는 사용자들을 나타냄

---

### HTTP Method

<html>
    <div style ="text-align:center">
        <img src= "https://s3.ap-northeast-2.amazonaws.com/urclass-images/M275pM7H5HPQz0iQbC9Hm-1660723179366.png" alt="HTTP Method" width="700" height="700">
    </div>
</html><br/>
