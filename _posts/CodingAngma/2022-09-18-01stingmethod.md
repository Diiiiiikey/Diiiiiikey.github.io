---
layouts: post
title:  "문자열과 문자열 메소드"
categories: JS
tag: [코딩앙마, string, string method, method]
toc: true
sidebar:
    nav: "docs"
---

## string

<ul>
<li>html 코드는 작은 따옴표로 감싸는 것이 좋다 내용에 큰따옴표가 있을 수 있기 때문이다.</li>
<li>영어 문장은 큰 따옴표로 감싸는 것이 좋다</li>
<li>.백틱은 ${}를 사용해서 변수를 표현하거나 표현식을 감쌀 수 있다.</li>
<li>백틱은 여러 줄을 포함할 수 있다. 따옴표로 줄을 바꾸고 샆다면 중간에 \n을 사용한다.</li>
<li>문자열도 length로 길이를 구할 수 있다.</li>
<li>문자열도 배열과 동일하게 [0]의 형태로 접근할 수 있다.</li>
<li>하지만 배열과 다르게 한글자만 바꾸는 것은 허용되지 않는다.</li>
</ul>

---

## string method

#### toUpperCase()

대문자로 바꾸기
```js
let decs = "Hi guys"
decs.toUpperCase(); // "HI GUyS"
```

---

<br/>

#### toLowerCase()

소문자로 바꾸기
```js
let decs = "Hi guys"
decs.toLowerCase(); // "hi guys"
```

---

<br/>

#### str.indexOf(text)

문자를 인수로 받아 몇번째에 위치하는지 알려준다.
```js
let desc = "Hi guys. Nice to meet you.";

desc.indexOf('to'); // 14
desc.indexOf('man') // -1
```
포함된 문자가 여러개라도 첫번째의 위치만 반환하기 때문에 주의해야 한다.

또한 if문을 사용할 때 주의해야 한다.
```js
if(desc.indexOf('Hi')// = 0) { 
    console.log('Hi가 포함된 문장입니다.');
}
```
찾으려는 문장이 맨 문자열 맨 앞에 있을 때의 index는 0이고 if문의 조건문에서 0은 false이기 때문에 출력되지 않는다 따라서
```js
if(desc.indexOf('Hi') > -1) { 
    console.log('Hi가 포함된 문장입니다.');
}
```
처럼 사용해야 한다.

<br/>

---

#### str.slice(n, m)

특정 범위의 문자열만 추출하는 방법<br/>
n부터 m까지의 문자열 추출<br/>
m이 없다면 문자열 끝까지<br/>
m이 있다면 포함은 안시킴<br/>
음수를 적으면 끝에서 부터 셈
```js
let desca = "abcdefg";
let descb = desca.slice(2, 5);
let descc = desca.slice(5);
let descd = desca.slice(2, -2);

console.log(descb); // cde
console.log(descc); // fg
console.log(descd); // cde
```

<br/>

---

#### str.substring(n, m);

str.slice와 마찬가지로 n과 m사이 문자열 반환<br/>
n과 m을 바꿔도 동작한다.<br/>
음수는 0으로 인식한다.
```js
let desc = "abcdefg"
desc.substring(2, 5); // "cde"
desc.substring(5, 2); // "cde"
```

---

<br/>

#### str.substr(n, m)

n부터 시작 m개를 가져옴
```js
let desc = "abcdefg"
desc.subst(2, 5); // "cdefg"
```

---

<br/>

#### str.includes

문자가 문자열에 있으면 true 없다면 false를 반환
```js
function hasSipal(str){
    if(str.includes('시팔')){
        console.log('금칙어가 있습니다.');
    }   else    {
        console.log('통과');
    }
}
```

---

<br/>

#### 문자열 비교

"a" < "c" = true<br/>
아스키코드표 "a".codePointAt(0); 97<br/>
반대로 String.fromCodePoint(9) "a"

---

<br/>

###### etc...

<ul>
<li>str.trim() 앞 뒤 공백 제거</li>
<li>str.repeat(n) n번 반복</li>
</ul>

###### 예문 1

```js
let list = [
"01. 들어가며",
"02. JS의 역사",
"03. 쟈료형",
"04. 함수",
"05. 배열",
];

let newList = [];

for(let i = 0; i < list.length; i++){
    newList.push(
        list[i].slice(4)
    );
}

console.log(newList);
```

<br/>

###### 예문 2

금칙어: 시팔
```js
function hasSipal(str){
    if(str.indexOf('시팔') > -1){
        console.log('금칙어가 있습니다.');
    }   else    {
        console.log('통과');
    }
}
```