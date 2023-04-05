---
layouts: post
title: "[Component & Hook]Function Component & Class Component"
categories: REACT
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

## Function Component & Class Component

Hook은 함수 컴포넌트 메소드

하지만 이전에는 클래스를 사용하여 리액트 앱을 개발했다.

### Class Component

---

```js
class Counter extends Component {
  constructor(props) {
    super(props);
    this.state = {
      counter: 0,
    };
    this.handleIncrease = this.handleIncrease.bind(this);
  }

  handleIncrease = () => {
    this.setState({
      counter: this.state.counter + 1,
    });
  };

  render() {
    return (
      <div>
        <p>You clicked {this.state.counter} times</p>
        <button onClick={this.handleIncrease}>Click me</button>
      </div>
    );
  }
}
```

복잡하고 상태 로직 재사용 어려움 -> 함수 컴포넌트 발달

상태 값을 사용하거나 최적화할 수 있는 기능 도입 - Hook

---

### Function Component

---

```js
function Counter() {
  const [counter, setCounter] = useState(0);

  const handleIncrease = () => {
    setCounter(counter + 1);
  };

  return (
    <div>
      <p>You clicked {counter} times</p>
      <button onClick={handleIncrease}>Click me</button>
    </div>
  );
}
```

---

### Hook 규칙

---

1. 리액트 함수 최상위에서만 호출
2. 리액트 함수 내에서만 사용

---
