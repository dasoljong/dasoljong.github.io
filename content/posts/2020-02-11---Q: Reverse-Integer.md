---
title: "Q: Reverse Integer"
date: "2020-02-11T23:46:37.121Z"
template: "post"
draft: false
slug: "Reverse Integer"
category: "CodeKata"
tags:
  - "CodeKata"
  - "Frontend"
  - "JavaScript"
description: "CodeKata Day2 - 정수 뒤집기"
socialImage: "/media/image-2.jpg"
---

## CodeKata : Reverse Integer

### 문제: 
<br>reverse 함수에 정수인 숫자를 인자로 받습니다.
<br>그 숫자를 뒤집어서 return해주세요.

<br>x: 숫자
<br>return: 뒤집어진 숫자를 반환!!

예들 들어,

x: 1234
<br>return: 4321

x: -1234
<br>return: -4321

x: 1230
<br>return: 321




### 풀이:

```js
const reverse = x => {
  let arr = [];
  let xStr = x.toString();

  for (let i = xStr.length - 1; i >= 0, i--) {
    if (xStr[i] === '-') {
      arr.unshift(xStr[i]);
    } else {
      arr.push(xStr[i])
    }
  }
  let makeOne = arr.join('')

  return parseInt(makeOne)
} 
```


### 해설<br>
인자로 들어오는 정수를 거꾸로 재배치하여 리턴하는 문제이다. 음수인 경우에 '-'만을 유지한채 나머지 숫자들을 거꾸로 재배치 하면 된다.
무언가를 재배치 해야할때 배열로 접근하면 문제가 보다 쉬워질 수 있다.
Arr로 빈 배열을 만들어주고, toString() 메소드로 인자로 들어온 x를 string으로 바꾸어 xStr 변수에 할당한다.

for 반복문을 뒤에서부터 돌려준다.
만약 xStr[i]의 값이 '-'인 경우, unshift 메소드를 사용하여 array의 맨 앞부분에 요소를 배열(추가) 시킨다.
그 외의 요소들은, push 메소드를 사용하여 순차적으로 array의 맨 뒷부분에 추가한다.

그 후, 완성된 arr를 join 메소드를 통하여 배열의 원소를 연결하여 하나의 값인 string으로 만들어준다.
그 string을 parseInt()함으로써 integer로 변환하여 리턴해준다.


### .join()

.join()은 배열의 원소들을 연결하여 하나의 값으로 만든다.

문법:
```css
var jbStr1 = jbAry.join();
````

jbAry 배열에 있는 원소들을 하나의 값으로 만듭니다. 원소들의 구분은 기본적으로 콤마(,)로 한다. 원소들의 구분을 다른 문자로 하려면 () 안에 원하는 문자를 넣는다.
위의 풀이와 같이 string으로만 만들고 싶다면, .join('') 으로 표시하면 된다.
```css
var jbStr2 = jbAry.join( ' / ' );
````


### .parseInt()

.parseInt()는 문자열을 정수로 바꾸는 함수이다. 만약 소수라면, 소수부분은 버린다.

문법:
```css
parseInt( string, n )
````

- string을 n진법일 때의 값으로 바꿉니다. n은 옵션으로 2부터 36까지 입력할 수 있습니다. 입력하지 않으면 10으로 처리합니다.
- string의 처리는 parseFloat()와 거의 같습니다.
- 소수 부분은 버립니다.
- 0x로 시작하면 16진법으로 처리합니다.