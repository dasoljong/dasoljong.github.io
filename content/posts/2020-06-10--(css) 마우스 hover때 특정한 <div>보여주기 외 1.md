---
title: "(css) 마우스 hover때 특정한 <div>보여주기 외 1"
date: "2020-06-10T09:46:37.121Z"
template: "post"
draft: false
slug: "마우스 hover때 특정한 <div>보여주기 외 1"
category: "css"
tags:
  - "React"
  - "Todo List"
  - "css"
  - "scss"
description: "마우스 hover때 특정한 <div>보여주기 외 1"
socialImage: "/media/image-2.jpg"
---

하단은 Todo List 컴포넌트의 한 부분이다.

```js
import React, { Component } from "react";
import "./TodoItem.scss";

class TodoItem extends Component {
  render() {
    const { text, checked, id, onToggle, onRemove } = this.props;

    return (
      <div className="todo-item" onClick={() => onToggle(id)}>
        <div
          className="remove"
          onClick={(e) => {
            e.stopPropagation();
            onRemove(id);
          }}
        >
          &times;
        </div>
    );
  }
}

export default TodoItem;
```

<br>
아래 두 가지 경우를 css를 통하여 적용해보자.

<h2>todo-item 에 마우스 오버를 할때, remove div 보이기</h2>

```css
.todo-item:hover .remove {
  opacity: 1;
}
```

<br>

<h2>todo-item 사이에 윗 테두리</h2>

```css
.todo-item + .todo-item {
  border-top: 1px solid #f1f3f5;
}
```

### reference

- https://velopert.com/3480-
