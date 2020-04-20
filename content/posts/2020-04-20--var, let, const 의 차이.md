---
title: "var, let, const의 차이"
date: "2020-04-20T09:46:37.121Z"
template: "post"
draft: false
slug: "var, let, const의 차이"
category: ""
tags:
  - "var"
  - "let"
  - "const"
  - "변수"
description: "var, let, const의 차이에 관하여 알아보자"
socialImage: "/media/image-2.jpg"
---

자바스크립트의 변수 선언 방식은 세가지로 나눌 수 있다.<br>
var, let, 그리고 const.

<h1>변수 선언 방식</h1>

<h3>1. var</h3>

```js
var name = "Daivd";
console.log(name); // David

var name = "John";
console.log(name); // John
```

위와 같이 var는 변수를 한번 더 선언 했음에도 불구하고 에러가 뜨지 않고 각기 다른 값이 출력 됨을 볼 수 있다.
간단한 코드 상에서는 편리할 수 있겠지만 코드가 길어지고 복잡해진다면 우리가 예상한 결과값이 나오지 않을 수 있다.

위와 같은 문제를 보완하기 위해서 나온 ES6의 변수 선언 방식이 let과 const다.

<h3>2. let & const</h3>

```js
let name = "Daivd";
console.log(name); // David

let name = "John";
console.log(name);
// Uncaught SyntaxError: Identifier 'name' has already been declared
```

위와 같이 변수 선언 방식을 var에서 let으로 바꾸어 보면 이미 선언되었다는 에러를 볼 수 있다.
(const로 바꾸어도 같은 에러가 등장한다.)<br>
즉, let과 const 모두 변수 재선언이 불가능하다.

그렇다면 let과 const의 차이는 무엇일까?
바로 재할당의 가능 불가능 여부이다.(immutable)

let 은 변수에 재할당이 가능하다. 그렇지만,

```js
let name = "Daivd";
console.log(name); // David

let name = "John";
console.log(name);
// Uncaught SyntaxError: Identifier 'name' has already been declared

name = "react";
console.log(name); // react
```

const는 변수 재선언, 변수 재할당 모두 불가능하다.

```js
const name = "Daivd";
console.log(name); // David

const name = "John";
console.log(name);
// Uncaught SyntaxError: Identifier 'name' has already been declared

name = "react";
console.log(name);
// Uncaught TypeError: Assignment to constant variable.
```

<h2>정리</h2>

- var : es5문법이며, let const와 다르게 호이스팅이 되어 변수의 스코프 범위가 컴포넌트 전체가 된다. (재선언, 재할당 가능)
- let : es6문법이며, var와 다르게 호이스팅이 안됨 (재선언 불가, 재할당 가능)
- const : es6문법이며, let과 마찬가지로 호이스팅이 안됨(재선언, 재할당 모두 불가)

변수 선언에는 기본적으로 const를 사용하고, 재할당이 필요한 경우에만 let을 사용하도록 한다. 이때, 변수의 scope는 최대한 좁게 만든다.

### reference

- https://velog.io/@bathingape/JavaScript-var-let-const-%EC%B0%A8%EC%9D%B4%EC%A0%90
