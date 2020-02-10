---
title: "Position of JVS(JVS의 위치)"
date: "2020-02-10T22:12:03.284Z"
template: "post"
draft: false
slug: "position-of-JVS"
category: "JavaScript"
tags:
  - "JVS"
  - "JavaScript"
  - "Frondtend"
description: "자바스크립트의 위치, 그리고 html 파일 내에서의 작성법에 대해 알아보자."
socialImage: "/media/gutenberg.jpg"
---

개발을 할 때는 java script 파일만으로는 javascript가 작동되진 않는다.
브라우저가 존재해야 하고, java script 파일을 호출하는 html 파일이 있어야 한다.

jvs 코드가 작성된 index.js 파일은 index.html에서 불러와주어야 한다.

<body> 태그 안쪽에 있어야 한다. 또한 body 태그 맨 아래에 위치시키야 문제 없이 jvs 코드를 읽어 올 수 있다. 

<script src="index.js"></script>


## html 파일 내에서의 jvs 코드 작성법

jvs 코드는 js 파일에만 작성해야 할 것 같지만 html 코드 내에도 jvs 코드를 작성할 수 있다.
But, html 파일 내의 <script> 태그 안에 jvs 코드를 작성해야만 한다. <script> 태그 내에 html 태그는 작성할 수 없다.

<script> 
  function sayHi() { 
    console.log('여기는 index.html파일입니다.'); 
  } 

  sayHi();
</script>
