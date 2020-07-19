---
title: "Q: merge sort를 만들어보자"
date: "2020-07-17T23:46:37.121Z"
template: "post"
draft: false
slug: "Merge sort"
category: "CodeKata"
tags:
  - "CodeKata"
  - "Frontend"
  - "JavaScript"
description: "merge sort를 만들어보자"
socialImage: "/media/image-2.jpg"
---

### 문제:

<br>1. 리스트의 길이가 0 또는 1이면 이미 정렬된 것으로 본다. 그렇지 않은 경우에는

<br>2. 정렬되지 않은 리스트를 절반으로 잘라 비슷한 크기의 두 부분 리스트로 나눈다.

<br>3. 각 부분 리스트를 재귀적으로 합병 정렬을 이용해 정렬한다.

<br>4. 두 부분 리스트를 다시 하나의 정렬된 리스트로 합병한다.

<br>다음 코드의 빈칸을 채워 병합정렬을 완성해 보자.

### 풀이:

아래와 같은 숫자 배열이 있다 가정하고 이를 계속해서 절반으로 자른다.<br>
[1, 3, 5, 4, 8, 6, 7, 2]<br>
[1, 3, 5, 4], [8, 6, 7, 2]<br>
[1, 3], [5, 4], [8, 6], [7, 2]<br>
[1], [3], [5], [4], [8], [6], [7], [2]<br>
이제 두 개씩 합쳐서 작은 것을 왼편으로 옮긴다.<br>
[1, 3], [4, 5], [6, 8], [2, 7]<br>
[1, 3, 4, 5], [2, 6, 7, 8]<br>
[1, 2, 3, 4, 5, 6, 7 ,8]<br>

첫 번째 라인부터 네 번째 라인까지는 나눠지는 부분이고, 그 밑은 합쳐지는 부분이다.<br>

```js
//분할부분
function mergeSort() {
  if (arr.length <= 1) {
    return arr;
  }

  const mid = Math.floor(arr.length / 2);
  const left = arr.slice(0, mid);
  const right = arr.slice(mid);

  return merge(mergeSort(left), mergeSort(right));
}

//정렬하고 합치는 부분
function merge() {
  let result = [];

  while (left.length && right.length) {
    if (left[0] < right[0]) {
      result.push(left.shift());
    } else {
      result.push(right.shift());
    }
  }
  while (left.length) {
    result.push(left.shift());
  }
  while (right.length) {
    result.push(right.shift());
  }
}

const array = [1, 3, 5, 4, 8, 6, 7, 2];
console.log(array); //[1, 3, 5, 4, 8, 6, 7, 2]
console.log(mergeSort(array)); //[1, 2, 3, 4, 5, 6, 7, 8]
```

### reference

- https://www.notion.so/51-merge-sort-217249ae47f2424baeab023685c90830
