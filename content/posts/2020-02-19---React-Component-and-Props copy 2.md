---
title: "React - Component"
date: "2020-02-19T23:46:37.121Z"
template: "post"
draft: false
slug: "React - Component"
category: "React"
tags:
  - "React"
  - "Frontend"
  - "JavaScript"
  - "JSX"
  - "Component"
  - "Props"
description: "Component"
socialImage: "/media/image-2.jpg"
---

# Component

컴포넌트란 재사용 가능한 UI 단위이다. 컴포넌트를 하나만 만들고 여기저기서 재사용하면, input 디자인이 바꼈을 때 css 한 줄만 수정하면 로그인, 회원가입, 내정보수정 페이지에 바뀐 디자인이 모두 반영될 것이다.
컴포넌트는 함수와 비슷하다. 함수도 기능이 독립적이고 재사용할 수가 있다. 컴포넌트 또한 input을 받아서 return 할 수 있다.


## Component 만들기

React는 컴포넌트를 만들고 관리하기 정말 좋은 라이브러리다. React에서는 컴포넌트를 class나 함수로 만들 수 있다. 


  ### 함수로 Welcome 컴포넌트 구현하기
```jsx
function Welcome(props){
  return <h1>Hello, {props.name}</h1>;
}
```


  ### class로 Welcome 컴포넌트 구현하기
```jsx
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

class로 컴포넌트를 만드려면 React.Component를 extend해서 생성해야한다. 컴포넌트를 생성할 때 render() 메소드는 무조건 정의해야 하고, return도 해주어야 한다.
render() 메소드를 무조건 정의해야 한다는 말은, component를 만들 때 필요한 메소드가 원래 더 있다는 말이다. 그런데 그 중에서 render()만 필수이다.


## Component 사용

위처럼 정의한 컴포넌트는 class/함수 이름으로 사용할 수 있따. 태그처럼 <Welcome />로 작성한다.
우리가 정의한 컴포넌트를 작성할 때, 원하는 attribute를 얼마든지 추가할 수 있다.
그러면 Welcome 컴포넌트(함수)에서 parameter로 해당 attribute를 받아서 사용할 수 있다. 이것을 props라고 한다. props는 property의 줄임말이다.
.(dot)으로 속성명에 접근 가능하고, props.속성명 으로 속성 값을 가져올 수 있다.

```jsx
// 1. Welcome 컴포넌트 정의
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}

// 2. App 컴포넌트 정의
class App extends React.Component {
  render() {
    return <div>
      <Welcome name="david" />
      <Welcome name="susan" />
  }
}

// 3. 화면에 React 요소 그려주기
ReactDOM.render(
  <App />,
  document.getElementById('root')
);

```

1. Welcome 컴포넌트: props.name의 값을 보면 name이라는 attribute를 부여했음을 알 수 있다.
2. App 컴포넌트를 보면 div로 감싸져 있고 <Welcome />를 두 번 사용했다. name이라는 attribute도 부여했다.
3. ReactDOM.render 함수로 React요소를 그려준다. root라는 id를 찾아 <App /> 컴포먼트를 그려준다.


### reference
- yeri-kim.github.io
