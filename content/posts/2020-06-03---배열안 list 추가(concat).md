---
title: "(React) 배열 안 list 추가(concat)"
date: "2020-06-03T23:46:37.121Z"
template: "post"
draft: false
slug: "배열 안 list 추가(concat)"
category: "React"
tags:
  - "Frontend"
  - "React"
description: "배열 안 list 추가(concat)"
socialImage: "/media/image-2.jpg"
---

배열에 리스트를 추가하기 위해서는 concat을 사용하면 된다.

```js
let ar = [10, 20, 30, 40, 50];
console.log(ar); //[10, 20, 30, 40, 50]

ar.concat(60);
console.log(ar); //[10, 20, 30, 40, 50]  //결과 값이 바뀐게 없음을 볼 수 있다.

ar = ar.concat(60);
console.log(ar); //[10, 20, 30, 40, 50, 60] //60이 추가 됨을 볼 수 있다.
```

<br>
아래 예시는 Todo list를 만들기 위해 작성한 코드이다.<br>
concat이 사용되었으니 참고하도록 하자.

```js
import React, { Component } from "react";

class Todo extends Component {
  state = {
    todayWork: ["테니스 레슨", "코딩 공부", "웨이트", "우유 산책"],
    name: "",
  };

  handleValue = (e) => {
    this.setState({
      name: e.target.value,
    });
    console.log(e.target.value);
  };

  handleAdd = (e) => {
    this.setState({
      todayWork: this.state.todayWork.concat(this.state.name),
      name: "",
    });
  };

  handleDelete = (i) => {
    this.setState({
      todayWork: [
        ...this.state.todayWork.slice(0, i),
        ...this.state.todayWork.slice(i + 1, this.state.todayWork.length),
      ],
    });
  };

  render() {
    const work = this.state.todayWork.map((today, i) => (
      <li key={i}>
        {today}
        <button onClick={() => this.handleDelete(i)}>삭제</button>
      </li>
    ));
    return (
      <div>
        <h1>Todo List</h1>
        <input
          type="text"
          name="name"
          value={this.state.name}
          placeholder="할 일을 적어주세요."
          onChange={this.handleValue}
        />
        <button onClick={this.handleAdd}>추가</button>
        <ul>{work}</ul>
      </div>
    );
  }
}

export default Todo;
```
