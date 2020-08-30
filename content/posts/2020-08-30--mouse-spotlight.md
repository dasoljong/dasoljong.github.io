---
title: "mouse-spotlight 구현하기"
date: "2020-08-30T09:41:37.121Z"
template: "post"
draft: false
slug: "mouse-spotlight"
category: "javascript"
tags:
  - "javascript"
  - "wecode"
description: "mouse-spotlight"
socialImage: "/media/image-2.jpg"
---

mouse-spotlight을 구현해보자.

<h2>html</h2>

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <link rel="stylesheet" href="slide.css" />
    <script src="slide.js" defer></script>
  </head>
  <body>
    <div class="slideshow-container">
      <div class="mySlides fade">
        <a>
          <img src="http://placehold.it/300x100" style="width: 100%;" />
        </a>
      </div>

      <div class="mySlides fade">
        <a>
          <img src="http://placehold.it/300x100" style="width: 100%;" />
        </a>
      </div>

      <div class="mySlides fade">
        <a>
          <img src="http://placehold.it/300x100" style="width: 100%;" />
        </a>
      </div>

      <a class="prev" onclick="plusSlides(-1)">&#10094;</a>
      <a class="next" onclick="plusSlides(1)">&#10095;</a>
    </div>
    <br />

    <div style="text-align: center;">
      <span class="dot" onclick="currentSlide(1)"></span>
      <span class="dot" onclick="currentSlide(2)"></span>
      <span class="dot" onclick="currentSlide(3)"></span>
    </div>
  </body>
</html>
```

<h2>javascript</h2>

```js
// 마우스 호버 이벤트 구역
const _mh = [];

// 블러 커버
_mh.blurCover = document.getElementById("blur-cover"); // 마우스 이동시 움직임 효과를 주기 위함
_mh.bigArea = document.getElementById("first-box"); // #first-box 내부에서만 함수가 실행될 수 있도록 조건 구역을 지정
_mh.bg = document.getElementsByClassName("bg").item(0); // 마우스 이벤트 동작시 등장 또는 사라지는 효과를 주기 위해 지정

_mh.mouse = function(e) {
  // 해상도 1920 x 938 기준으로 맞춤

  // 스크롤 높이 위치 값
  const scrollY = document.documentElement.scrollHeight;

  // 해상도의 넓이값과 높이값을 참조
  const screenX = window.innerWidth / 2;
  const screenY = window.innerHeight / 2 - scrollY;

  // 마우스 위치값과 해상도 값을 계산하여 배경 위치 조정
  const x = e.clientX - screenX;
  const y = e.clientY - screenY;

  // 마우스 인 기능 구현
  if (this == _mh.bigArea) {
    _mh.bg.style.opacity = "1";
  }

  console.log("마우스 인");

  _mh.blurCover.style.backgroundPosition = "" + x + "px " + y + "px";
};

// 마우스 아웃 기능 구현
_mh.mouseOut = function(e) {
  _mh.bg.style.opacity = "0";

  console.log("마우스 아웃");
};

// 사용자가 마우스를 움직이는경우 함수 실행
_mh.bigArea.addEventListener("mousemove", _mh.mouse);
_mh.bigArea.addEventListener("mouseout", _mh.mouseOut);
```

<h2>css</h2>

```css
.bg {
  background-image: url("https://search.pstatic.net/common?type=o&size=120x171&quality=100&direct=true&src=https%3A%2F%2Fs.pstatic.net%2Fmovie.phinf%2F20181019_236%2F1539926790655oHv5z_JPEG%2Fmovie_image.jpg%3Ftype%3Dw640_2");
  background-size: auto;
  padding-bottom: 50%;
  position: absolute;
  width: 100%;
  top: 0;
  left: 0;
  opacity: 0;
  transition: 0.3s all;
}

.bg #blur-cover {
  background-repeat: no-repeat;
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  /*background-color: #333;*/
  background: -moz-radial-gradient(
    circle closest-side,
    transparent,
    rgba(255, 255, 255, 1) 300px
  );
  background: -webkit-radial-gradient(
    circle closest-side,
    transparent,
    rgba(255, 255, 255, 1) 300px
  );
  background: -ms-radial-gradient(
    circle closest-side,
    transparent,
    rgba(255, 255, 255, 1) 300px
  );
  background: -o-radial-gradient(
    circle closest-side,
    transparent,
    rgba(255, 255, 255, 1) 300px
  );
}
```

<!--
### reference

- https://velog.io/@haileyself/TIL-Ajax-fetch-promise-uak0t7wne7 -->
