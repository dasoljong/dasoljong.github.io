---
title: "(React) Todo list, Enter로 Input 입력하기"
date: "2020-06-05T09:46:37.121Z"
template: "post"
draft: false
slug: "Todo list, Enter로 Input 입력하기"
category: ""
tags:
  - "Vue.js"
description: "Todo list, Enter로 Input 입력하기"
socialImage: "/media/image-2.jpg"
---

프로젝트를 진행할 때, 편의성을 위해 자주 적용되는 이벤트 중 하나가 엔터 키를 눌렀을 때 어떠한 종류의 버튼을 클릭되게 하는 것이다.<br>
하단의 Todo 코드를 통해 해당 내용을 살펴보자.

```js
  // (소스 생략)...

  handleAdd = (e) => {
    this.setState({
      todayWorks: this.state.todayWorks.concat(this.state.name),
      name: "",
    });
  };

  handleEnter = (e) => {
    if (e.key === "Enter") {
      this.handleAdd();
    }
  };

  render() {
    return (
      <div>
        <h1>Todo List</h1>
        <input
          type="text"
          name="name"
          value={this.state.name}
          placeholder="할 일을 입력하세요."
          onChange={this.handleValue}
          onKeyPress={this.handleEnter}
        />
        <button onClick={this.handleAdd}>추가</button>
      </div>
    );
  }
}

export default Todo;
```

상기 코드의 핵심은 이벤트 key 값이 Enter와 일치하면 클릭 이벤트를 호출 한다는 것이다.
<br>

---

<br>
하단의 코드는 React를 통해 만든 Todo list이다.<br>
기록을 위해 남겨둔다.

```js
import React, { Component } from "react";

class Todo extends Component {
  state = {
    todayWorks: ["축구", "아침 먹기", "약국 가기", "코딩 공부", "우유 산책"],
    name: "",
  };

  handleValue = (e) => {
    this.setState({
      [e.target.name]: e.target.value,
    });

    console.log(e.target.value);
  };

  handleAdd = (e) => {
    this.setState({
      todayWorks: this.state.todayWorks.concat(this.state.name),
      name: "",
    });
  };

  handleDelete = (i) => {
    this.setState({
      todayWorks: [
        ...this.state.todayWorks.slice(0, i),
        ...this.state.todayWorks.slice(i + 1, this.state.todayWorks.length),
      ],
    });
  };

  handleEnter = (e) => {
    if (e.key === "Enter") {
      this.handleAdd();
    }
  };

  render() {
    return (
      <div>
        <h1>Todo List</h1>
        <input
          type="text"
          name="name"
          value={this.state.name}
          placeholder="할 일을 입력하세요."
          onChange={this.handleValue}
          onKeyPress={this.handleEnter}
        />
        <button onClick={this.handleAdd}>추가</button>
        <ul>
          {this.state.todayWorks.map((work, i) => (
            <li key={i}>
              {work}
              <button onClick={() => this.handleDelete(i)}>삭제</button>
            </li>
          ))}
        </ul>
      </div>
    );
  }
}

export default Todo;
```

<!--
### reference

- https://velog.io/@bathingape/JavaScript-var-let-const-%EC%B0%A8%EC%9D%B4%EC%A0%90 -->
