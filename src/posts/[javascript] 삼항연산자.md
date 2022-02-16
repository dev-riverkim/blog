---
title: javascript 응용 - 삼항연산자
description: javascript 응용 - 삼항연산자
permalink: posts/{{ title | slug }}/index.html
date: "2022-02-16"
tags: [javascript, 삼항연산자]
---

## 삼항연산자

삼항연산자의 사용법

> 조건 ? true일때 : false일때

```javascript
const arr = [];
let text = "";

if (arr.length === 0) {
  text = "배열이 비어있습니다.";
} else {
  text = "배열이 비어있지 않습니다.";
}

console.log(text);
```

위의 코드를 삼항연산자로 변경

```javascript
const arr = [];
let text = arr.length === 0 ? "배열이 비어있습니다." : "배열이 비어있지 않습니다.";

console.log(text);
```

삼항 연산자를 중첩해서 쓸 수도 있지만 가독성이 좋지 않아서 사용을 권장하지 않음
