---
layouts: post
title:  "JS 코딩앙마 기초 5"
categories: JS
tag: [코딩앙마, 논리연산자]
toc: true
sidebar:
    nav: "docs"
---

## 논리연산자

<html>
|| <br/>
or: 하나라도 true 면 true, 첫번째 true를 발견하면 즉시 평가를 멈춤 <br/>
</html>

            a || b

<br/>
<br/>

<html>
&& <br/>
And: 하나라도 false 면 false, 첫번째 false를 발견하면 즉시 평가를 멈춤<br/>
</html>

            a && B

<br/>
<br/>

<html>
! <br/>
Not: true 와 false의 반대값을 출력 <br/>
</html>

            !a

<br/>
<br/>
<br/>

```js
const name = "MIKE";
const age = 30;

if(name === 'TOM' || age > 19){
    console.log('통과');
}
```

이름은 일치하지 않지만 나이가 19세 이상이기 때문에 통과

<br/>

```js
if(name === 'TOM' && age > 19){
    console.log('통과');
}   else    {
    console.log('불가');
}
```

이름이 일치하지 않기 때문에 불가

<br/>

```js
const age = prompt("나이");
const isAge = age >= 19;
        
if(!isAge){
    console.log('돌아가세요');
}   else    {
    console.log('환영합니다');
}
```

나이를 입력했을 때 19세 이상이 아니라면 "돌아가세요" 아니라면 "환영합니다"

<br/>

```js
const gender = "F";
const name = "John";
const isAdult = true;

if(gender === "M" && name === "Mike" || isAdult){
    console.log("통과");
}   else    {
    console.log("안돼");
}
```

and가 or보다 우선순위가 높기 때문에 먼저 평가된다. 남자이고 이름도 Mike 이지만 성인이기 때문에 통과

<br/>

```js
if(gender === "M" && (name === "Mike" || isAdult)){
    console.log("통과");
}   else    {
    console.log("안돼");
}
```

위와 반대로
or가 and보다 우선순위가 높아졌기 때문에 "안돼"