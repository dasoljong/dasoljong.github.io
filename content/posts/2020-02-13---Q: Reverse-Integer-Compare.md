---
title: "Q: Reverse Integer and Compare"
date: "2020-02-13T23:46:37.121Z"
template: "post"
draft: false
slug: "Reverse Integer"
category: "CodeKata"
tags:
  - "CodeKata"
  - "Frontend"
  - "JavaScript"
description: "CodeKata Day4 - 정수 뒤집고 비교"
socialImage: "/media/image-2.jpg"
---

## CodeKata : Reverse Integer and Comapare

### 문제:

숫자인 num을 인자로 넘겨주면, 뒤집은 모양이 num과 똑같은지 여부를 반환해주세요.

<br>num: 숫자
<br>return: true or false (뒤집은 모양이 num와 똑같은지 여부)

<br><br>예를 들어,
<br>num = 123
<br>return false
<br>=> 뒤집은 모양이 321 이기 때문

<br>num = 1221
<br>return true
<br>=> 뒤집은 모양이 1221 이기 때문

<br>num = -121
<br>return false
<br>=> 뒤집은 모양이 121- 이기 때문

<br>num = 10
<br>return false
<br>=> 뒤집은 모양이 01 이기 때문

### 풀이

```js
const sameReverse = num => {
  let str = String(num);
  let arr = [];

  for (let i = str.length - 1; i >= 0; i--) {
    arr += str[i];
  }

  if (arr == num) {
    return true;
  } else {
    return false;
  }
};
```

### 해설 <br>

앞선 Reverse Integer question과 같은 방식으로 접근하였다. 우선 인자를 string으로 바꾸어주고 뒤에서부터 for문을 통해 빈 배열에 넣어주었다.
그 후, num과 arr이 같은지 비교한다.
