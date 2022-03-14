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

const results = runners.map((runner, i) => ({
  name: runner,
  race,
  place: i + 1,
}));

console.log(results);
// [
//   { name: "Usain Bolt", race: "100m dash", place: 1 },
//   { name: "Justin Gatlin", race: "100m dash", place: 2 },
//   { name: "Asafa Powell", race: "100m dash", place: 3 },
// ];
```

이 예에서는 map함수를 사용하여 runners 배열에 대한 반복을 구현한다.
첫 번째 인수 runner는 배열의 현재 원소고, i는 배열의 인덱스이다.
배열의 각 원소에 대해 name,race,place속성을 포함하는 객체를 results에 추가한다.

중괄호 안에 있는 것이 암시적으로 반환하려는 객체 리터럴임을 자바스크립트에 알리려면, 전체 괄호 안에 감싸야 한다.

여기서 race를 쓰나 race:race를 쓰나 모두 결과는 동일하다.

# 2.3 화살표 함수는 익명함수

이전 예제에서 볼 수 있듯이 화살표 함수는 익명 함수이다.
참조할 이름이 필요하다면 함수를 변수에 할당하면 된다.

```javascript
const greeting = (name) => `hello ${name}`;
greeting("Tom");
```

# 2.4 화살표 함수와 this 키워드

화살표 함수 내부에서 this 키워드를 사용할 때는 일반 함수와 다르게 동작하므로 주의해야 한다.

화살표 함수를 사용할 때 this 키워드는 상위 스코프에 상속된다.
