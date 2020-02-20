---
title: "React - Named/Default export"
date: "2020-02-20T09:46:37.121Z"
template: "post"
draft: false
slug: "React - Named/Default export"
category: "React"
tags:
  - "React"
  - "Frontend"
  - "JavaScript"
  - "export"
  - "import"
description: "Named/Default export"
socialImage: "/media/image-2.jpg"
---

# export

파일이나 모듈 안의 함수나, 객체를 export 하는데 사용된다.
export에는 Named exports와 Default exports 두 가지 방법이 있다.


## Named exports

Named exports는 여러 값을 export하는데 유용하다. export 된 이름을 사용하여 import하여 사용할 수 있다.

아래와 같이 export 할 수 있다.

```jsx
// module "my-module.js"
function cube(x) {
    return x * x * x;
}
const foo = Math.PI + Math.SQRT2;
export { cube, foo };
```

위의 export된 값들을 import하여 사용할 때 아래와 같이 사용할 수 있습니다.

```jsx
import { cube, foo } from 'my-module';
console.log(cube(3)); // 27
console.log(foo);    // 4.555806215962888
```


## Default exports

모듈 당 딱 한 개의 default export만 있어야 한다. default export로 객체, 함수 클래스 등이 될 수 있다.
가장 간단하게 export 할 수 있으며 딱 한개만 default export를 할 수 있기에 가장 메인이라 할 수 있는 것을 default export하는 것이 좋다.

아래와 같이 Default export 할 수 있다.

```jsx
// module "my-module.js"
let cube = function cube(x) {
    return x * x * x;
}
export default cube;
```

default exports된 값을 import 하는 방법은 아래와 같습니다.

```jsx
// module "my-module.js"
import myFunction from 'my-module';
console.log(myFunction(3)); // 27
```



### reference
- https://beomy.tistory.com/22