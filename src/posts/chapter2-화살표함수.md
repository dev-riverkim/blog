---
title: chapter2 - 화살표함수
description: 모던자바스크립트 핵심가이드 정리
permalink: posts/{{ title | slug }}/index.html
date: "2022-03-14"
tags: [javascript, 화살표함수]
---

# 2.1 화살표 함수

ES6에서 뚱뚱한 화살표(=>)를 사용해서 함수를 선언하는 방법인 화살표 함수가 처음 도입되었다.
ES5에서 일반적으로 함수를 선언하는 방법은 아래와 같다.

```javascript
const greeting = function (name) {
  return "hello " + name;
};
```

이를 화살표 함수로 바꾸면 다음과 같다.

```javascript
var greeting = (name) => {
  return `hello + ${name}`;
};
```

매개변수가 하나만 있으면 괄호를 생략이 가능하다.

매개변수가 전혀 없으면 아래와 같이 빈 괄호를 사용한다.

```javascript
var greeting = () => {
  return "hello";
};
```

# 2.2 암시적 반환

화살표 함수를 사용하면 명시적인 반환을 생략하고 다음과 같이 반환할 수 있다.

```javascript
const greeting = (name) => `hello ${name}`;
```

ES5의 함수와 나란히 비교해보자

```javascript
const oldFunction = function (name) {
  return "hello " + name;
};

const arrowFunction = (name) => `hello ${name}`;
```

두 함수 모두 결과는 같지만, 새로 도입된 문법을 사용하면 코드가 더 간결해진다.

하지만 주의하자! 코드의 간결함보다 더 중요한 것은 가독성이다.
팀 단위의 프로젝트에서 모든 팀원이 ES6의 문법을 숙지하지는 못했다면, 함수를 다음과 같이 작성하는 것이 좋다.

```javascript
const arrowFunction = (name) => {
  return `hello + ${name}`;
};
```

객체 리터럴을 암시적으로 반환해야 한다면, 다음과 같은 코드를 사용할 수 있다.

```javascript
const race = "100m dash";
const runners = ["Usain Bolt", "Justin Gatlin", "Asafa Powell"];
```
