---
layouts: post
title:  "Virtual DOM"
categories: JS
tag: [codestates]
toc: true
sidebar:
    nav: "docs"
---

## Virtual DOM

React에는 가상의 DOM 객체가 있다(Vritual DOM)

실제 DOM의 사본 같은 개념, React는 실제 DOM 객체가 아닌 가상의 DOM 객체에 접근, 전 후를 비교하고 바뀐 부분만 적용

---

### DOM(Real DOM)
---
JavaScript와 같은 스크립팅 언어가 `<html>, <head>, <body>`와 같은 태그들에 접근하고 조작할 수 있도록 태그들을 트리 구조로 객체화 시킨 것, 즉 브라우저가 트리 구조로 만든 객체 모델

<html>
    <div style ="text-align:center">
        <img src= "https://user-images.githubusercontent.com/58800295/180721685-95fb88e0-05a3-48b5-a798-17ab95e9665f.png" alt="DOM" width="700" height="700">
    </div>
</html><br/>

DOM은 UI 상태가 변경될 때마다 해당 변경 사항을 나타내기 위해 업데이트됨, DOM을 조작하는 정도가 잦다면 성능에 영향, DOM의 렌더링은 브라우저의 파워, 즉 브라우저의 구동 능력에 의존하기 때문에 DOM의 조작 속도는 느려짐

---

### DOM의 조작 속도가 느려지는 이유
---
DOM의 구조는 계층적 구조의 트리, 트리는 저장된 데이터를 더 효과적으로 탐색을 위함, 따라서 DOM은 JavaScript와 같은 스크립팅 언어가 접근하고 탐색하는 속도가 빠르기 때문에 변경 및 업데이트 속도 또한 빠름.

but,

DOM이 업데이트가 된다는 것은 결국 브라우저의 렌더링 엔진 또한 리플로우(Reflow)한다는 것

DOM 트리를 재구축함으로써 재랜더링 과정을 거쳐 UI를 업데이트 해야 됨

브라우저의 리플로우와 리페인트 과정은 레이아웃 및 페인트에 해당하는 재연산을 해야 하기 때문에 속도가 느려짐

e.g. 6개의 컨텐츠 중 하나만 변경해도 변경된 컨텐츠와 함께 다른 5개 또한 업데이트 된다.

바뀐 부분만 비교해서 렌더링하자 - Virtual DOM 탄생

---

### Virtual DOM
---
가상 DOM 객체는 내용을 직접 변경하는 것은 아님

- 가상의 UI 요소를 메모리에 유지
- 유지시킨 가상의 UI 요소를 ReactDOM과 같은 라이브러리를 통해 실제 DOM과 동기화

실제 DOM을 조작하는 것은 브라우저 화면에 그리기 때문에 느림, 가상 DOM은 화면에 그리는 것이 아니기 때문에 속도가 빠름

---

### 가상 DOM이 빠른 이유
---

1. 상태가 변경이 되면 다시 새로운 가상의 DOM 트리가 만들어짐
2. 이전의 가상의 DOM과 이후의 가상의 DOM의 차이 비교
3. 가상의 DOM은 실제 DOM에 변경을 수행할 수 있는 최상의 방법을 계산
4. 실제 DOM은 최소한의 작업만 수행해도 렌더링 가능

<html>
    <div style ="text-align:center">
        <img src= "https://user-images.githubusercontent.com/58800295/180723292-06084835-9194-46c5-a712-b2fa8ed94c86.png" alt="Virtual DOM update" width="700" height="700">
    </div>
</html><br/>

---

### Virtual DOM 형태
---
<html>
    <div style ="text-align:center">
        <img src= "https://user-images.githubusercontent.com/58800295/180723370-be6c5a5f-cd9c-42bb-9bf7-baed8fba9fe6.png" alt="Virtual DOM 형태" width="700" height="700">
    </div>
</html><br/>

```js
const vDom = {
	tagName: "html",
	children: [
		{ tagName: "head" },
		{ tagName: "body",
			children: [
				tagName: "ul",
				attributes: { "class": "list"},
				children: [
					{
						tagName: "li",
						attributes: { "class": "list_item" },
						textContent: "List item"
					}
				]
			]
		}
	]
}
```

