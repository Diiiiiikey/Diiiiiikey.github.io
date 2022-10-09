---
layouts: post
title:  "연습 1"
categories: JS
tag: [노마드코더]
toc: true
sidebar:
    nav: "docs"
---

1. console.dir 을 사용하면 document를 호출할 수 있다.
   ## 1번 예시

console.dir(title); 을 통해서 더 자세하게 객체의 형태로 id를 관찰할 수 있고
textContent: "Grab me!" 등
을 통해서 JS를 통해서 HTML을 읽을 수 있다는 것을 알 수 있다.

2. title을 보면 Momentum이라고 되어있는데 우리는 js에서 title을 정의한적이 없다.
3. document가 HTML을 JS의 관점의 object로 보여준다.
4. JS는 HTML에 접근하고 읽을 수 있게 설정이 되어 있다. 
5. JS에서 document.title = "JS"를 하면 타이틀이 바뀐다.
6. html에서 타이틀을 HTML로 바꾸고 js에서 title을 JS로 바꾸었을 때 JS로 나온다.
   ## 6번 예시

HTML
```html
<h1 id="title">Grab me!</h1>
```

JS
```js
const title = document.getElementById("title");
title.innerText = "good!"
```
일 때 title로 good!이 나온다.

7. console에서 document.body를 사용하면 html의 body부분을 가져올 수 있다.







