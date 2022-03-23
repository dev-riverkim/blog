---
title: chapter3 - 함수 기본값 인수
description: 모던자바스크립트 핵심가이드 정리
permalink: posts/{{ title | slug }}/index.html
date: "2022-03-22"
tags: [javascript, 인수]
---

# 3.1 함수 인수의 기본값(ES6 이전)

ES6 이전에는 함수 인수의 기본값을 설정하는 것이 쉽지 않았다.

```javascript
function getLocaion(city, country, continent) {
  if (typeof country === "undefined") {
    country = "Italy";
  }
  if (typeof continent === "undefined") {
    continent = "Europe";
  }

  console.log(continent, country, city);
}
// city만 적은 상태
getLocaion("Milan"); // Europe Italy Milan
// city와 country만 적은 상태
getLocaion("Paris", "France"); // Europe France Paris
```

예제의 함수는 city,country,continent 세 가지 인수를 취한다.
함수 본문에서 country 또는 continent가 정의되지 않았는지 확인하고,
정의되지 않은 경우에만 기본값을 제공

기본값이 인수 목록의 끝이 아닌 시작 부분에 있도록하려면

```javascript
function getLocaion(continent, country, city) {
  if (typeof country === "undefined") {
    country = "Italy";
  }
  if (typeof continent === "undefined") {
    continent = "Europe";
  }

  console.log(continent, country, city);
}

getLocaion(undefined, undefined, "Milan");
getLocaion(undefined, "Paris", "Milan");

// Europe Italy Milan
// Europe Paris Milan
```

# 3.2 함수 기본값 인수

ES6에서는 함수 기본값 인수를 매우 쉽게 설정할 수 있다.

```javascript
function calculatePrice(total, tax = 0.1, tip = 0.05) {
  // tax나 tip에 값을 할당하지 않으면 기본값으로 0.1과 0.05가 쓰인다.
  return total + total * tax + total * tip;
}

// 매개변수를 아예 전달하지 않으려면?
// tip에 0.15를 할당하려 했지만, 아래처럼 쓰면 0.15는 두 번째 인수 tax에 할당된다.
calculatePrice(100, 0.15);

// 이렇게 쓰면 tip에 0.15를 할당하게 된다.
// 깔끔한 방법은 아니다.
calculatePrice(100, undefined, 0.15);
```

디스트럭처링을 통해 코드를 개선 할 수 있다.

```javascript
function calculatePrice({ total, tax = 0.1, tip = 0.05 } = {}) {
  // tax나 tip에 값을 할당하지 않으면 기본값으로 0.1과 0.05가 쓰인다.
  return total + total * tax + total * tip;
}

const bill = calculatePrice({ tip: 0.15, total: 150 });

console.log(bill); //187.5
```

함수의 인수를 객체로 만들었다.
함수를 호출하면 매개변수가 주어진 키에 맞춰서 입력되기 때문에
매개변수의 순서에 대해 걱정할 필요가 없다.

앞의 예에서는 tip의 기본값은 0.05이지만 0.15로 덮어 썼고, tax는 값을
덮어 쓰지 않아 기본값인 0.1로 유지되었다.

{ total, tax = 0.1, tip = 0.05 } = {}
여기서 인수 객체를 빈 객체로 기본 설정하지 않고(즉={}를 빼고) 선언한 다음
아무 매개변수도 없이 calculatePrice()를 실행하면 다음과 같은 오류가 발생한다.

TypeError: Cannot destructure property 'total' of 'undefined' as it is undefined.

= {}를 추가해야 인수를 기본적으로 객체로 설정한다.
함수에 매개변수를 어떻게 전달하든 상관없이 인수는 객체가 된다.
