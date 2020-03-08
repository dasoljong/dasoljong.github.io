---
title: "(CSS) CSS 우선순위 "
date: "2020-02-26T01:46:37.121Z"
template: "post"
draft: false
slug: "CSS - 우선순위"
category: "React"
tags:
  - "Frontend"
  - "JavaScript"
  - "CSS"
description: "CSS의 우선순위에 대하여 알아보자"
socialImage: "/media/image-2.jpg"
---

웹 사이트를 제작하다보면 하나의 태그에 여러 가지의 CSS가 적용될 때가 있다. 이 때 특정한 규칙에 따라 CSS에 우선 순위가 부여되어 적용된다.
이러한 규칙을 CSS 우선순위라 한다.

규칙은 아래와 같다.

- 기본적으로 뒤에 나오는 CSS가 우선순위가 높다.
- !important > inline style attribute > id > class. 다른 attribute, 수도클래스(:first-child 같은 것) > tag element, 수도 엘레먼트(::before 같은 것) 순으로 우선순위가 높다.
- 우선순위가 같다면 개수가 많은 css가 우선순위가 높다.

위 규칙을 숙지한다면 대부분의 CSS에 적용할 수 있을것이다.

### reference

- https://www.zerocho.com/category/CSS/post/588cb95ca63e64132496a5d5
