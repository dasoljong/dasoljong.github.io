---
title: "(React) defaultProps & propTypes"
date: "2020-06-11T09:46:37.121Z"
template: "post"
draft: false
slug: "defaultProps & propTypes"
category: "React"
tags:
  - "React"
  - "JavaScript"
  - "defaultProps"
  - "propTypes"
description: "defaultProps & propTypes"
socialImage: "/media/image-2.jpg"
---

컴포넌트의 필수 props를 지정하거나 props의 타입(type)을 지정할 때는 propTypes를 사용하면 된다.<br>
또한, props의 기본값을 설정하기 위해서는 defaultProps를 사용하면 된다.<br>
아래 코드를 살펴보자.

<h2>클래스형 컴포넌트</h2>

```js
class MyComponent extends Component {
  static defaultProps = {
    name: "기본 이름",
  };

  static propTypes = {
    name: PropTypes.string,
    favoriteNumber: PropTypes.number.isRequired,
  };

  render() {
    const { name, children, favoriteNumber } = this.props;
    return (
      <div>
        안녕하세요, 제 이름은 {name} 입니다.
        <br />
        children 값은 {children} 입니다.
        <br />
        제가 좋아하는 숫자는 {favoriteNumber} 입니다.
      </div>
    );
  }
}

export default MyComponent;
```

<br>
<h2>함수형 컴포넌트</h2>

```js
const MyComponent = ({ name, children, favoriteNumber }) => {
  return (
    <div>
      안녕하세요, 제 이름은 {name} 입니다.
      <br />
      children 값은 {children} 입니다.
      <br />
      제가 좋아하는 숫자는 {favoriteNumber} 입니다.
    </div>
  );
};

MyComponent.defaultProps = {
  name: "기본 이름",
};

MyComponent.propTypes = {
  name: PropTypes.string,
  favoriteNumber: PropTypes.number.isRequired, //propTypes와 함께 isRequired를 있다면, proptypes를 지정하지 않으면 콘솔에 에러 문구가 뜬다.
};

export default MyComponent;
```

<br>
defaultProps와 propTypes를 필수 사항이 아니다. 사용 유무는 개인의 선택이지만 대형 프로젝트를 진행할 때 사용한다면 많은 오류를 줄일 수 있다..

### reference

- (서적) 리액트를 다루는 기술 by 김민준(VELOPERT)
