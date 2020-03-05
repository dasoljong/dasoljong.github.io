---
title: "React - state"
date: "2020-02-20T08:46:37.121Z"
template: "post"
draft: false
slug: "React - state"
category: "React"
tags:
  - "React"
  - "Frontend"
  - "JavaScript"
  - "JSX"
  - "Component"
  - "Props"
  - "state"
  - "setState"
description: "state & setState"
socialImage: "/media/image-2.jpg"
---

# State

정해진 데이터를 다룰떈 props, 동적인 데이터를 다룰땐 state를 사용한다. 
아래 Counter 라는 파일을 생성해서 새로운 컴포넌트를 만들어 보았다.

```jsx
import React, { Component } from 'react';

class Counter extends React.Component {

  state = {
    number: 0
  }

  handleIncrease = () => {
    this.setState({
      number: this.state.number + 1
    });
  }

  handleDecrease = () => {
    this.setState({
      number: this.state.number - 1
    });
  }

  render() {
    return (
      <div>
        <h1>카운터</h1>
        <div>값: {this.state.number}</div>
        <button onClick={this.handleIncrease}>+</button>
        <button onClick={this.handleDecrease}>-</button>
      </div>
    );
  }
}

export default Counter;
```
## state 정의

함수를 정의할때, 위처럼 arrow 함수를 사용하지 않고 아래와 같이 사용하는 경우도 있다.

```jsx
handleIncrease() {
  this.setState({
    number: this.state.number + 1
  })
}

handleDecrease() {
  this.setState({
    number: this.state.number - 1
  })
}
```
위와 같은 경우에는 아래와 같이 constructor(props)와 super(props)를 호출해줘야 한다.

```jsx
class Counter extends React.Component {
  state = {
    number: 0
  }
  
  constructor(props) {
    super(props);
    this.handleIncrease = this.handleIncrease.bind(this);
    this.handleDecrease = this.handleDecrease.bind(this);
    }
  }

  handleIncrease() {
    this.setState({
      number: this.state.number + 1
    })
  }

  handleDecrease() {
    this.setState({
      number: this.state.number - 1
    })
  }

  ....


}

```

위를 본다면 class fields를 사용하는게 더 편리함을 알 수 있다.


## setState

this.setState에 대해 알아보자. state에 있는 값을 바꾸기 위해서는, this.setState를 무조건 거쳐야한다. 
리액트에서는 이 함수가 호출되면 컴포넌트가 리렌더링 되도록 설계되어 있다. 또한, setState는 객체로 전달되는 값만 업데이트를 해준다.


## 이벤트 설정

render 함수에서 이벤트 설정을 한 부분을 확인해보자.

```jsx
render() {
  return (
    <div>
      <h1>카운터</h1>
      <div>값: {this.state.number}</div>
      <button onClick={this.handleIncrease}>+</button>
      <button onClick={this.handleDecrease}>-</button>
    </div>
  );
}
```

위 코드의 이벤트중 onClick 속성을 살펴보자.
여기서 우리가 주의해야 할 점이 있다.
 - 이벤트 이름을 설정할 때, camelCase로 설정해야한다. 
 - 이벤트에 전달하는 값은 함수여야 한다. 아래와 같이 작성하게 된다면 큰 일이 발생할 수 있다.

 ```jsx 
 onClick={this.handleIncrease()}
 ```

위의 식으로 하게 된다면, 렌더링을 할 때 마다 해당 함수가 호출된다.
렌더링 -> 함수 호출 -> setState -> 렌더링 -> 함수 호출 -> 무한반복.. 

위와 같이 작성을 끝냈다면 해당 컴포넌트를 App에 불러와서 렌더링을 해보자.

```jsx
import React, { Component } from 'react';
import Counter from './Counter';

class App extends React.Component {
  render() {
    return (
      <Counter />
    );
  }
}

export default App;
```

### reference
- https://react-anyone.vlpt.us/04.html