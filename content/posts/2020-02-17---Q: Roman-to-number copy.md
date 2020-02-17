---
title: "Q: Roman to Number"
date: "2020-02-17T23:46:37.121Z"
template: "post"
draft: false
slug: "Roman to Number"
category: "CodeKata"
tags:
  - "CodeKata"
  - "Frontend"
  - "JavaScript"
description: "CodeKata W2 Day1 - 로마자에서 숫자로 바꾸기"
socialImage: "/media/image-2.jpg"
---

## CodeKata : Roman to number

### 문제: 

로마자에서 숫자로 바꾸기
<br><br>
1~3999 사이의 로마자 s를 인자로 주면 그에 해당하는 숫자를 반환해주세요.
<br>로마 숫자를 숫자로 표기하면 다음과 같습니다.

Symbol       Value
<br>I             1
<br>V             5
<br>X             10
<br>L             50
<br>C             100
<br>D             500
<br>M             1000

로마자를 숫자로 읽는 방법은 로마자를 왼쪽부터 차례대로 더하면 됩니다.
<br>III = 3
<br>XII = 12
<br>XXVII = 27
<br>입니다.

그런데 4를 표현할 때는 IIII가 아니라 IV 입니다.
<br>뒤의 숫자에서 앞의 숫자를 빼주면 됩니다. 
<br>9는 IX입니다.

I는 V와 X앞에 와서 4, 9
<br>X는 L, C앞에 와서 40, 90
<br>C는 D, M앞에 와서 400, 900 


### 풀이

```js
function romanToNum(s) {
  let result = 0;
  const roman = {
    I: 1,
    V: 5,
    X: 10,
    L: 50,
    C: 100,
    D: 500,
    M: 1000
  };
  
  for (let i = 0; i < s.length; i++) {
    let currentNum = roman[s[i]];
    let nextNum = roman[s[i+1]];
    
    if (currentNum < nextNum) {
      result =  result - currentNum;
    } else {
      result = result + currentNum;
    }
  }
  return result;
}
```

### 해설 <br>
결국 숫자의 총 합을 구해야 하는 문제이기에 for문으로 접근하였다.
이 문제를 해결할때 주의할 점은 아래 조건을 생각해야 한다는 점이다.

<br>///
<br>그런데 4를 표현할 때는 IIII가 아니라 IV 입니다.
<br>뒤의 숫자에서 앞의 숫자를 빼주면 됩니다. 
<br>9는 IX입니다.

<br>I는 V와 X앞에 와서 4, 9
<br>X는 L, C앞에 와서 40, 90
<br>C는 D, M앞에 와서 400, 900 
<br>///

<br>보통의 경우는, 뒤의 인자가 앞의 인자보다 작지만, 위의 조건에서는 앞의 인자보다 뒤의 인자가 더 크다.
<br>그 특이점을 통하여 if문으로 접근하였다.


