---
title: "React - Props"
date: "2020-02-19T07:46:37.121Z"
template: "post"
draft: false
slug: "React - Props"
category: "React"
tags:
  - "React"
  - "Frontend"
  - "JavaScript"
  - "JSX"
  - "Component"
  - "Props"
description: "Props & defaultProps"
socialImage: "/media/image-2.jpg"
---

# Props

리엑트 컴포넌트에서 다루는 데이터는 두개로 나뉜다. 바로 props와 state이다.
props는 부모 컴포넌트가 자식 컴포넌트에게 주는 값이다. 자식 컴포넌트는 부모 컴포넌트로부터 props를 받아오기만 하고, 받아온 props를 직접 수정할 수 없다.

반면 state 는 컴포넌트 내부에서 선언하며 내부에서 값을 변경 할 수 있다.


## 새 Component 만들기

src 디렉토리에 MyName이라는 컴포넌트를 만들어보자.

```jsx
import React, { Component } from 'react';

class MyName extends React.Component {
  render() {
    return(
      <div>
        안녕하세요! 제 이름은 <b>{this.props.name}</b>입니다.
      </div>
    );
  }
}

export default MyName;
```

받아온 props 값은 <b>this.</b> 키워드를 통하여 조회할 수 있다. 지금 name 이라는 props를 보여주도록 설정하였다.
이제 이 컴포넌트를 사용해보자.

App.js를 다음과 같이 열어보라.

```jsx
import React, { Component } from 'react';
import MyName from './MyName';

class App extends React.Component {
  render(){
    return (
      <MyName name='david' />
    );
  }
}

export default App;
```

import를 통해 컴포넌트를 불러오고, 렌더링해보자. 이렇게 컴포넌트를 만들고 나면 일반 태그를 작성하듯 작성해주면 된다.
그리고 props 값은, name='david' 이런 식으로 태그의 속성을 설정해주는 것 처럼 해주면 된다.

작성 후 브라우저를 확인해보면 아래와 같은 화면을 볼 수 있다.

안녕하세요! 제 이름은 <b>daivd</b>입니다.


## defaultProps

종종 실수로 props를 빠뜨릴 때도 있다. 혹은 특성 상황에서는 props를 일부러 비워두어야 할 때도 있다.
이런 경우에 props의 기본값을 설정할 수 있는데 그것이 바로 defaultProps이다.

```jsx
import React, { Component } from 'react';

class MyName extends React.Component {

  static defaultProps = {
    name: 'david'
  };

  render() {
    return (
      <div>
        안녕하세요! 제 이름은 {this.props.name}입니다.
      </div>
    );
  }
}

export default MyName;

```
이런 식으로 작성 후, App.js(부모 컴포넌트)에 <MyName /> 이런 식으로 name 값을 생략해버리면 'david'가 나타나게 될 것이다.
defaultProps는 아래와 같은 형식으로도 작성 할 수 있으며 결과값은 같다.

```jsx
import React, { Component } from 'react';

class MyName extends React.Component {

  render() {
    return (
      <div>
        안녕하세요! 제 이름은 {this.props.name}입니다.
      </div>
    );
  }
}

MyName.defaultProps = {
  name: 'david'
};

export default MyName;

```

## 함수형 컴포넌트

이렇게 단순히 props만 받아와서 보여주기만 하는 컴포넌트의 경우엔 더욱 간편한 문법으로 작성할 수 있는 방법이 있다.
바로, 함수형태로 작성하는 것이다.

```jsx
import React from 'react';

const MyName = ({ name }) => {
  return (
    <div>
      안녕하세요! 제 이름은 {name}입니다.
    </div>
  );
};

MyName.defaultProps = {
  name: 'david'
};

```

### reference
- https://react-anyone.vlpt.us/04.html