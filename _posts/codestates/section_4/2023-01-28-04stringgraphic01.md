---
layouts: post
title: "[STRING]문자열"
categories: COMPUTER
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

프로그래밍 언어마다 문자열을 저장하는 자료형은 다 다르고 용량도 다름

## 유니코드

유니코드 협회(Unicode Consortium)가 제정하는 전 세계의 모든 문자를 컴퓨터에서 일관되게 표현하고 다룰 수 있도록 설계된 산업 표준

유니코드의 목적은 현존하는 문자 인코딩 방법을 모두 유니코드로 교체하는 것

---

### 인코딩(부호화)

---

어떤 문자나 기호를 컴퓨터가 이용할 수 있는 신호로 만드는 것

인코딩과 디코딩의 기준을 문자열 세트 또는 문자셋(charset). 문자셋의 국제 표준이 유니코드

---

## ASCII 코드

영문 알파벳을 사용하는 대표적인 문자 인코딩. 7 비트로 모든 영어 알파벳을 표현. 52개의 영문 알파벳 대소문자와, 10개의 숫자, 32개의 특수 문자, 그리고 하나의 공백 문자를 포함

유니코드는 ASCII를 확장한 형태

---

## UTF-8과 UTF-16 차이점

인코딩 방식의 차이

Universal Coded Character Set + Transformation Format – 8-bit의 약자, UTF- 뒤에 숫자는 비트

- UTF-8 특징

  - 가변 길이 인코딩

    유니코드 한 문자를 나타내기 위해 1 byte(= 8 bits)에서 4bytes까지 사용

    - 원리
      코 - 유니코드는 U+CF54(16진수, HEX), 이진법(binary number)으로 1100-1111-0101-0100, UTF-8로

      ```js
        1110xxxx 10xxxxxx 10xxxxxx
          // x 안에 순서대로
        11101100 10111101 10010100
      ```

      ```js
      let encoder = new TextEncoder(); // 기본 인코딩은 'utf-8'
      encoder
        .encode("코")(
          // Uint8Array(3) [236, 189, 148]

          236
        )
        .toString(2)(
          // "11101100"
          189
        )
        .toString(2)(
          // "10111101"
          148
        )
        .toString(2); // "10010100"
      ```

    - ASCII 코드는 7비트로 표현, UTF-8로 1 byte
      ```js
      encoder
        .encode("b")(
          // Uint8Array [98]
          98
        )
        .toString(2); // "1100010"
      ```

  - 바이트 순서 고정

    UTF-16에 비해 바이트 순서를 따지지 않고, 순서 고정

- UTF-16 특징

  - 코드 그대로 바이트로 표현 가능, 바이트 순서 다양

    - 유니코드 코드 대부분(U+0000부터 U+FFFF; BMP)을 16 bits로 표현
      - 기타 문자는 32 bit(4 bytes)로 표현, UTF-16도 가변 길이라고 할 수 있으나, 대부분은 2 바이트로 표현
    - U+ABCD 16진수 그대로 이진법으로 변환, 1010-1011-1100-1101, 16 bits(2 bytes)로 그대로 사용, 순서(엔디언)에 따라 UTF-16의 종류 달라짐

UTF-8에서는 한글은 3 바이트, UTF-16에서는 2 바이트
