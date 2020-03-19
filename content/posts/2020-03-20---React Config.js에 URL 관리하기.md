---
title: "(React) 간편하게 URL 관리하기 "
date: "2020-03-16T09:46:37.121Z"
template: "post"
draft: false
slug: "config.js 파일에 URL 관리하기"
category: "React"
tags:
  - "React"
  - "Frontend"
  - "URL"
description: "config.js 파일에 URL 관리하기"
socialImage: "/media/image-2.jpg"
---

우리는 fetch를 사용하며 서버 URL을 자주 사용하게 된다. fetch가 한 두번 사용된다면 괜찮겠지만 여러 곳에서 여러번 사용된다 가정해보자.
어떠한 이유로 해당 URL을 바꿔야 한다면 우리는 fetch가 사용된 모든 파일을 수정해야 할 것이다. 그러다 보면 실수 할 가능성이 높아진다.
하지만, config 파일에 반복되는 URL을 저장하고 사용한다면 수정이 필요할 때, 단 한번만 수정하면 될 것이다. 아래 예시를 통해 살펴보자.<br><br>

## 1. config.js 파일에 URL 저장하기.

wezard 프로젝트에서 실제로 구현했던 코드를 참고해보자.

/config.js

```js
export const Address = "http://10.58.2.253:8000";
export const AWS = "http://52.78.241.65:8000";
export const URL = "http://10.58.7.135:8000";
```

위와 같이 config.js 파일 안에 세개의 URL을 각각의 변수에 저장하였다.

변수에 저장된 다양한 URL들을 아래와 같이 사용할 수 있다.

```js
import React from 'react';
import { URL } from "../../../config"

  componentDidMount() {
    const queryId = this.props.location.search.split("=")[1];
    const end = queryId + 4;
    // console.log("id", queryId);

    fetch(`${URL}/article/detail/${end}`)
      .then(res => res.json())
      .then(res => {
        // console.log("드러와:", res.data);
        this.setState(
          {
            data: res.data[0]
          },
          () => {
            console.log(this.state.data);
          }
        );
      });
  }

```

위와 같이, 변수 URL을 사용하기 위해서는 먼저 import 해준 후, 백틱을 통해 URL을 호출한다.

코드 작성 후 URL 수정 시, 유지 보수 면에서 훨씬 빠르고 정확성이 보장됨을 느낄 수 있다.

### reference

- https://medium.com/@ghur2002/react%EC%97%90%EC%84%9C-infinite-scroll-%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0-128d64ea24b5
