---
layouts: post
title:  "고차함수"
categories: JS
tag: [codestates]
toc: true
sidebar:
    nav: "docs"
---


## 일급 객체(first-class citizen)

대표적으로 함수

JS에서 함수는

1. 변수에 할당(assignment) 가능
2. 다른 함수의 전달인자(argument)로 전달 가능
3. 다른 함수의 결과로서 리턴 가능


---


## 고차 함수

고차함수(higher order function)는 함수를 전달인자(argument)로 받을 수 있고, 함수를 리턴할 수 있는 함수

다른 함수(caller)의 전달인자(argument)로 전달되는 함수를 콜백 함수(callback function)

1. 다른 함수를 인자로 받음

    형태
    ```js
    function double(num) {
    return num * 2;
    }

    function doubleNum(func, num) {
    return func(num);
    }

    let output = doubleNum(double, 4);
    console.log(output); // -> 8
    ```

2. 함수를 리턴

    형태
    ```js
    function adder(added) {
        return function (num) {
            return num + added;
        };
    }

    let output = adder(5)(3); // -> 8
    console.log(output); // -> 8

    const add3 = adder(3);
    output = add3(2);
    console.log(output); // -> 5
    ```

3. 함수를 받고 함수를 리턴
   
   형태
   ```js
    function double(num) {
    return num * 2;
    }

    function doubleAdder(added, func) {
    const doubled = func(added);
        return function (num) {
            return num + doubled;
        };
    }
   ```


---


## 내장고차함수


filter, map, reduce, forEach, find, sort, some, every 등

아무래도 문제를 많이 풀어봐야 알 것 같다.


---


막혔던 coplit

6번

