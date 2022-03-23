---
title: chapter5 - 문자열 메서드
description: 모던자바스크립트 핵심가이드 정리
permalink: posts/{{ title | slug }}/index.html
date: "2022-03-23"
tags: [javascript, 문자열 메서드]
---

# 5.1 기본적인 문자열 메서드

자바스크립트에는 문자열에 사용할 수 있는 많은 메서드가 있다.

## indexOf()

문자열에서 지정된 값이 처음 나타나는 위치를 반환한다.

```javascript
const str = "this is a short sentence";
const result = str.indexOf("short");

console.log(result); // 10
```

## slice()

문자열의 지정된 부분을 새 문자열로 반환한다.

```javascript
const str = "pizza, orange, cereals";
const result = str.slice(0, 5);

console.log(result); // pizza
```

## toUpperCase()

문자열 내의 모든 문자를 대문자로 바꾼다.

```javascript
const str = "i ate an apple";
const result = str.toUpperCase();

console.log(result); //I ATE AN APPLE
```

## toLowerCase()

문자열의 모든 문자를 소문자로 바꾼다

```javascript
const str = "I ATE AN APPLE";
const result = str.toLowerCase();

console.log(result); // i ate an apple
```

# 5.2 새로운 문자열 메서드

ES6는 4가지 새로운 문자열 메서드를 도입했다.

- startsWith()
- endsWith()
- includes()
- repeat()

## startsWith()

이 메서드는 매개변수로 받은 값으로 문자열이 시작하는지 확인한다.

```javascript
const code = "ABCDEFG";

const result1 = code.startsWith("ABB");
console.log(result1); // false
const result2 = code.startsWith("abc");
console.log(result2); // false
const result3 = code.startsWith("ABC");
console.log(result3); // false
```

매개 변수를 추가로 전달하면 메서드가 검사를 시작하는 시작점을 지정할 수도 있다.

```javascript
const code = "ABCDEFG";
const result4 = code.startsWith("DEF", 3);
console.log(result4); // true
```

## endsWith()

startsWith()와 유사하게 문자열이 우리가 전달한 값으로 끝나는지 확인

```javascript
const code = "ABCDEF";

const result1 = code.endsWith("DDD");
console.log(result1); // false

const result2 = code.endsWith("def");
console.log(result2); // false

const result3 = code.endsWith("DEF");
console.log(result3); // true
```

추가 매개변수로 문자열의 얼마큼만을 확인할지 길이를 전달할 수 있다.

```javascript
const code = "ABCDEFGHI";

const result4 = code.endsWith("EF", 6);
console.log(result4); // true

const result4 = code.endsWith("EF", 7);
console.log(result4); // false

const result4 = code.endsWith("EF", 4);
console.log(result4); // false
```

첫 6개 문자인 ABCDEF만을 고려하며, ABCDEF는 EF로 끝나므로 true

## includes()

이 메서드는 우리가 전달한 값이 문자열에 포함되어 있는지 확인한다.

```javascript
const code = "ABCDEF";

const result1 = code.includes("ABB");
console.log(result1); // false

const result2 = code.includes("abc");
console.log(result2); // false

const result3 = code.includes("CDE");
console.log(result3); // true
```

## repeat()

문자열을 반복하며 횟수를 인수로 받는다.

```javascript
let hello = "Hi";
console.log(hello.repeat(10)); // HiHiHiHiHiHiHiHiHiHi
```
