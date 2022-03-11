---
title: chapter0 - 자바스크립트기초
description: 모던자바스크립트 핵심가이드 정리
permalink: posts/{{ title | slug }}/index.html
date: "2022-02-16"
tags: [javascript]
---

# 0.1 변수

변수는 값을 담기위한 공간이다.
예를들면, 사용자 이름, 주소, 쇼핑몰 사이트의 상품 항목 등등의 값을 저장하기 위해 변수를 사용

ES6(ES2015) 이전에는 아래와 같이 변수 선언

```javascript
var username = "riverkim";
```

ES6(ES2015) 이후에는 아래와 같이 변수 선언

```javascript
let username = "riverkim";
const username = "riverkim";
```

const 키워드로 생성된 변수는 이름에서 알 수 있듯 상수이므로 그 값을 덮어 쓸 수 없다.

```javascript
const age = 26;
age = 27;

// 오류 발생
```

```javascript
let height = 190;
height = 189;

// 값이 정상적으로 변경 됨
```

```javascript
// 변수명은 숫자로 시작할 수 없음
let 1apple ="one apple";
// 변수명에는 공백,기호, 마침표가 들어갈 수 없음
let hello! ='hello!';
```

변수 이름을 선택할때는 변수 이름 자체가 변수를 설명할 수 있도록 하면 좋다.

# 0.2 자료형

자바스크립트는 동적인 언어이다.
즉, 정적 언어와 달리 변수를 정의할 때 자료형을 정의할 필요가 없다.

```javascript
var userID;
userID = 12;
console.log(typeof userID); // number
userID = "user1"; // 문자열 할상
console.log(typeof userID); // string
```

자바스크립트에는 총 7개 자료형이 있다. 6개는 원시 자료형이고 나머지 하나는 객체다.

## 원시 자료형

원시자료형은 객체가 아닌 자료형으로, 메서드를 가지지 않는다.

- string : 문자열
  - 텍스트 데이터를 나타내는데 사용
- number : 숫자
  - 숫자로 된 값을 나타내는데 사용
- boolean : 불리언
  - true(참) 또는 false(거짓)값을 나타내는데 사용
- null : 널
  - 값이 없음
- undefined : 정의되지 않음
  - 정의되지 않은 값
- symbol : 심벌, ES6에서 추가 됨
  - 고유하고 변경할 수 없는 값

## 객체

앞의 6개 원시 자료형은 null 값이든, true든, false든 하나의 값만 담을 수 있지만
객체는 여러 속성의 모음을 저장하는 데 사용

```javascript
const car = {
  wheels: 4,
  color: "red",
};
```

차의 속성을 저장하는 데 사용하는 간단한 객체이다.
각 속성에는 키와 값이 있다.

키의 자료형은 string 자료형 이지만 값은 모든 자료형이 될 수 있으며, 심지어 함수가 될 수도 있다.
값이 함수이면 메서드를 호출하는 셈이다.

```javascript
const car = {
  wheels: 4,
  color: "red",
  drive: function () {
    console.log("부릉 부릉");
  },
};

console.log(Object.keys(car)[0]); // wheels
console.log(typeof Object.keys(car)[0]); // string

car.drive(); // 부릉부릉
```

## 빈 객체 생성하기

객체를 생성할 때에는 속성을 선언할 필요가 없다.

빈 객체를 만드는 방법에는 다음과 같이 두 가지 방법이 있다.

```javascript
const car = new Object();
const car = {};
```

두 번째 방법이 더 일반적으로 사용되는데, 이를 '객체 리터럴' 이라고도 부른다.

```javascript
const car = {};
car.color = "red";
// {color:'red'}
```

점 표기법을 사용해 car 객체에 새 속성을 추가

객체의 속성에 접근할 때는 점 표기법과 대괄호 표기법 두 가지 방법이 있다.

```javascript
const car = {
  wheels: 4,
  color: "red",
};

console.log(car.wheels); // 4
console.log(car["color"]); // red
```

두 방법이 완전히 동일하지는 않음
여러 단어로 이뤄진 속성의 경우 점 표기법 사용 불가능

```javascript
const car = {
  wheels: 4,
  color: "red",
  "goes fast": true,
};


console.log(car.goes fast); // error
console.log(car["goes fast"]) // true
```

대괄호 표기법을 사용하는 또 다른 경우는 키를 사용해서 객체의 속성에 접근할 때

```javascript
const cars = {
  ferrari: "california",
  porsche: "911",
  bugatti: "veyron",
};

// 사용자 입력
const key = "ferrari";

console.log(cars.key); // undefined
console.log(cars["key"]); // undefined
console.log(cars[key]); // california
```

변수에 저장된 키를 통해 객체의 속성에 접근하려면 대괄호 표기법을 사용해야 한다.

## 객체의 복사

원시 자료형과는 달리 객체를 복사할 때는 참조방식이 쓰인다.

```javascript
let car = {
  color: "red",
};

let secondCar = car;
```

여기서 secondCar는 그 자체로 객체가 아니라 car에 대한 참조, 즉 주소를 저장한다.
