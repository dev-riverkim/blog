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

```html
<div class="box open"> This is a box </div>
```

```css
.opening {
  background-color: red;
}
```

```javascript
// box 클래스를 가진 div를 가져온다
const box = document.querySelector(".box");

// 클릭 이벤트 핸들러를 등록
box.addEventListener("click", function () {
  console.log("클릭됨");
  this.classList.toggle("opening");
  console.log(this); // box 엘리먼트
  setTimeout(function () {
    // 클래스를 다시 토글
    console.log(this); // window
    this.classList.toggle("opening");
  }, 500);
});

// Uncaught TypeError: Cannot read properties of undefined (reading 'toggle')
```

이 코드의 문제는, 첫 번째 this 가 const box에 할당되었지만 setTimeout내부의 두 번째 this는 Window객체로 설정되어 다음과 같은 오류가 발생한다는 점

화살표 함수가 부모 스코프에서 this의 값을 상속한다는 것을 인지하면, 다음과 같이 함수를 다시 작성 할 수 있다.

```javascript
// box 클래스를 가진 div를 가져온다
const box = document.querySelector(".box");

// 클릭 이벤트 핸들러를 등록
box.addEventListener("click", function () {
  console.log("클릭됨");
  this.classList.toggle("opening");
  console.log(this); // box 엘리먼트
  setTimeout(() => {
    // 클래스를 다시 토글
    console.log(this); // box 엘리먼트
    this.classList.toggle("opening");
  }, 500);
});
```

여기서 두 번째 this는 부모로부터 상속되며 const box로 설정된다.

# 2.5 화살표 함수를 피해야 하는 경우

this 키워드의 상속에 대해 알았으니, 화살표 함수를 사용하면 문제가 될 수 있는 상황을 정리해보자.

다음 예는 화살표 함수에서 this를 주의해서 사용해야 하는 경우이다.

```javascript
const button = document.querySelector("btn");

button.addEventListener("click", () => {
  // 오류: 여기서 this는 Window 객체를 가리킴
  this.classList.toggle("on");
});
```

다음과 같은 예도 마찬가지다.

```javascript
const person1 = {
  age: 10,
  grow: function () {
    this.age++;
    console.log(this.age);
  },
};
person1.grow(); // 11

const person2 = {
  age: 10,
  grow: () => {
    this.age++; // 오류 여기서 this는 Window 객체를 가리킴
    console.log(this.age);
  },
};

person2.grow();
```

화살표 함수와 일반 함수의 또 다른 차이점은 arguments 객체에 대한 접근 방식이다.

arguments객체는 내부 함수에서 접근할 수 있는 배열 객체이며, 해당 함수에 전달된 인수의 값을 담고 있다.

간단한 예를 살펴보자

```javascript
function example() {
  console.log(arguments[0]);
}

example(1, 2, 3); // 1
```

이와 같이 배열 표기법 arguments[0]을 사용하면 첫 번째 인수에 접근할 수 있다.
this 키워드와 비슷하게, 화살표 함수에서 arguments 객체는 부모 스코프의 값을 상속한다.

앞에서 본 예제의 runners 배열을 응용한 다음 예를 살펴보자

```javascript
const showWinner = () => {
  const winner = arguments[0];
  console.log(`${winner} was the winner`);
};

showWinner("Usain Bolt", "Justin Gatlin", "Asafa Powell");
//arguments is not defined
```

함수에 전달된 모든 인수에 접근하려면, 기존 함수표기법이나 스프레드문법을 사용하면 된다.

여기서 arguments는 변수 이름이 아니라 키워드라는 점에 유의하자..

화살표 함수로 arguments에 접근하는 예는 다음과 같다.

```javascript
const showWinner = (...args) => {
  const winner = args[0];
  console.log(`${winner} was the winner`);
};

showWinner("Usain Bolt", "Justin Gatlin", "Asafa Powell");
// Usain Bolt was the winner
```

위 코드를 일반함수로 구현하면 다음과 같다.

```javascript
const showWinner = function () {
  const winner = arguments[0];
  console.log(`${winner} was the winner`);
};

showWinner("Usain Bolt", "Justin Gatlin", "Asafa Powell");
```
