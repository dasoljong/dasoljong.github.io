---
title: "Old version of package 인스톨 방법"
date: "2020-03-31T07:46:37.121Z"
template: "post"
draft: false
slug: "old version of package로 돌아가기"
category: ""
tags:
  - "Vue.js"
  - "Frontend"
description: "old version of package로 돌아가기 & 돌아갈 수 있는 버전 확인법"
socialImage: "/media/image-2.jpg"
---

많은 경우는 아니지만 우리는 종종 과거 버전의 package 돌아가야 할 경우가 생긴다.

그럴땐 아래의 명령어를 사용하자

`npm install <package>@<version>`

만약 어떤 버전으로 되돌아 갈 수 있는지 확인하고 싶다면 아래 명령어를 입력하면 확인할 수 있다.

```npm view <package> versions

```

### reference

- https://stackoverflow.com/questions/15890958/how-to-install-a-previous-exact-version-of-a-npm-package
