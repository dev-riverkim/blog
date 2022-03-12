---
title: chapter0 - 자바스크립트기초
description: 모던자바스크립트 핵심가이드 정리
permalink: posts/{{ title | slug }}/index.html
date: "2022-03-11"
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

- string : 문자열 => 텍스트 데이터를 나타내는데 사용
- number : 숫자 => 숫자로 된 값을 나타내는데 사용
- boolean : 불리언 => true(참) 또는 false(거짓)값을 나타내는데 사용
- null : 널 => 값이 없음
- undefined : 정의되지 않음 => 정의되지 않은 값
- symbol : 심벌, ES6에서 추가 됨 => 고유하고 변경할 수 없는 값

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

```javascript
let car = {
  color: "red",
};

let secondCar = car;

car.wheels = 4;
consol.log(car); // {color:'red', wheels:4}
consol.log(secondCar); // {color:'red', wheels:4}
```

secondCar는 단순히 car에 대한 참조만 저장하기 때문에 car를 수정하면 secondCar도 변경된다.

```javascript
console.log(car == secondCar); // true
console.log(car === secondCar); // true
```

==을 사용하든 ===를 사용하든 true가 반환된다.

```javascript
const emptyObj1 = {};
const emptyObj2 = {};

console.log(emptyObj1 == emptyObj2); // false
console.log(emptyObj1 === emptyObj2); // false

const obj1 = { a: 1 };
const obj2 = { a: 1 };

console.log(obj1 == obj2); // false
console.log(obj1 === obj2); // false
```

동일한 객체를 비교할 때만 true를 반환받을 수 있음

자바스크립트에서 객체의 복사본을 만드는 빠른 방법 중 하나는 Object.assign()을 사용하는 방법

```javascript
const car = {
  color: "red",
};

const secondCar = Object.assign({}, car);
car.wheel = 4;
console.log(car); // {color:'red', wheel:4}
console.log(secondCar); // {color:'red'}
```

위 방법을 사용하면 car을 업데이트해도 secondCar에는 영향을 주지 않는다.
Object.assign()의 첫 번째 인수는 복사본에 해당하는 객체이고, 두 번째 인수는 원본에 해당하는 객체이다.
위의 예시에서는 빈 객체를 복사본으로 넣고, car를 원본으로 넣었다.

## 배열

배열은 순서대로 값을 저장하는 객체

위에서 car를 저장하기 위해 객체를 사용한 이우는 키를 통해 쉽게 접근 할 수 있다는 특징이 있기 때문
하지만 항목으로 이뤄진 목록만 저장할 때는 객체를 만들 필요가 없다. 배열을 사용하면 된다.

```javascript
const fruitBasket = ["apple", "banana", "orange"];
```

위와 같이 만들어진 배열의 각 항목의 값에 접근할 때는 인덱스를 사용하면 된다.
배열의 인덱스는 0부터 시작한다.

```javascript
const fruitBasket = ["apple", "banana", "orange"];
console.log(fruitBasket[0]); // apple
console.log(fruitBasket[1]); // banana
console.log(fruitBasket[2]); // orange
```

배열에 대해 호출할 수 있는 많은 메서드가 있다.

```javascript
const fruitBasket = ["apple", "banana", "orange"];
// 배열의 길이를 확인
console.log(fruitBasket.length); // 3

// 배열의 끝에 새 값을 추가
fruitBasket.push("peer");
console.log(fruitBasket); // ['apple', 'banana', 'orange', 'peer']

// 배열의 시작에 새 값을 추가
fruitBasket.unshift("melon");
console.log(fruitBasket); // ['melon', 'apple', 'banana', 'orange', 'peer']

// 배열의 끝에서 값 하나를 제거
fruitBasket.pop();
console.log(fruitBasket); // ['melon', 'apple', 'banana', 'orange']

// 배열의 시작에서 값 하나를 제거
fruitBasket.shift();
console.log(fruitBasket); // ['apple', 'banana', 'orange']
```

위와 같은 메서드를 사용하여 배열의 시작 또는 끝에서 원소를 쉽게 추가하고 제거할 수 있다.

## typeof를 사용해서 자료형 확인하기

typeof를 사용하면 변수가 어떤 값을 담았는지 알 수 있다.

```javascript
const str = "hello";
console.log(typeof str); // string

const num = 12;
console.log(typeof num); // number

const arr = [1, 2, 3];
console.log(typeof arr); // object

const obj = { prop: "value" };
console.log(typeof obj); // object
```

배열은 원시(기본) 자료형이 아니라 객체다!

```javascript
console.log(typeof null); // object
```

null은 원시(기본) 자료형이기 때문에 결과가 null이 되어야 하지만
자바스크립트를 구현할 때 버그로 object로 출력

# 0.3 함수

함수는 온갖 계산과 작업을 수행하는 데 쓰이는 매우 중요한 도구
자바스크립트에서 함수를 선언하는 방법은 몇 가지가 있다.

```javascript
function greet(name) {
  // name은 매게변수(파라미터), {}안의 코드는 명령문
  console.log("hello " + name);
}

greet("riverkim");

// hello riverkim
```

여기서 중요한 점은 원시 자료형이 함수에 전달될 때는 참조가 아니라 값의 형태로 전달된 다는 점
이는 해당 값에 대한 변경 사항이 전역적으로 반영되지 않음을 의미
반면, 원시 자료형이 아닌 객체나 배열을 함수에 전달할 때는 참조로 전달된다.
즉, 해당 값에 대한 수정 사항이 원래의 객체에 반영된다.

```javascript
let myInt = 1;
function increase(value) {
  return (value += 1);
}

console.log(myInt); // 1
console.log(increase(myInt)); // 2
console.log(myInt); // 1
```

위의 예제에서는 정수의 값을 증가시켰지만, 원래 변수에는 영향을 주지 않았음.

반면, 객체를 사용한 예를 들어보면

```javascript
let myCar = {
  maker: "bmw",
  color: "red",
};

console.log(myCar); // {maker: 'bmw', color: 'red'}

function changeColor(car) {
  car.color = "blue";
}

changeColor(myCar);
console.log(myCar); // {maker: 'bmw', color: 'blue'}
```

매개변수 car는 객체 myCar에 대한 참조에 불과하므로,
이를 수정하면 myCar객체도 변경된다는 것을 볼 수 있다.

함수를 선언하는 또 다른 방법은 함수표현식을 사용하는 방법

```javascript
const greeter = function greet(name) {
  console.log("hello " + name);
};

greeter("riverkim");

// hello riverkim
```

greeter라는 const에 greet 함수를 할당

함수표현식을 사용하여 익명함수를 만들 수도 있다.

아래는 익명 함수를 사용하는 예(결과는 앞의 예제와 동일)

```javascript
const greeter = (name) => {
  console.log("hello " + name);
};

greeter("riverkim");
// hello riverkim
```

# 0.4 함수 스코프와 this 키워드의 이해

스코프는 자바스크립트에서 이해해야 할 가장 중요한 개념

## 스코프

변수의 스코프란 변수에 접근할 수 있는 위치를 제어한다.
전역 스코프를 가지는 변수는 코드의 어느 곳에서나 접근할 수 있다.
블록 스코프를 가지는 변수는 변수가 선언된 블록 내부에서만 접근할 수 있다.

여기에서 블록은 함수, 루프, 혹은 중괄호({})로 구분되는 모든 영역을 의미한다.

먼저 키워드 var를 사용하는 두 가지 예

```javascript
var myInt = 1;
if (myInt === 1) {
  var mySecondInt = 2;
  console.log(mySecondInt); // 2
}
console.log(mySecondInt); // 2
```

var 키워드로 선언된 변수 mySecondInt는 블록 스코프를 가지지 않기 때문에 블록 외부에서도 그 값에 접근할 수 있다.

let 키워드를 사용하는 예

```javascript
var myInt = 1;
if (myInt === 1) {
  let mySecondInt = 2;
  console.log(mySecondInt); // 2
}
console.log(mySecondInt); // 오류 [Uncaught ReferenceError: mySecondInt is not defined]
```

이번에는 에러가 난다.
let 또는 const 키워드로 선언된 변수는 변수가 선언된 위치에 해당하는 블록 스코프를 가지게 된다.

## this 키워드

this 키워드는 스코프에 이어 두 번째로 중요한 개념

```javascript
const myCar = {
  color: "red",
  logColor: function () {
    console.log(this.color);
  },
};

myCar.logColor(); // red
```

this의 값은 함수가 호출되는 방식에 따라 다르다.
위의 예에서 함수는 객체의 메서드로 호출되었다.

```javascript
function logThis() {
  console.log(this);
}

logThis();
// Window
```

위의 함수는 전역 범위에서 호출했으므로 this 값은 window 객체를 참조한다.
스트릭 모드로 설정하면 실수로 window 객체를 참조하는 것을 방지할 수 있다.

스트릭 모드를 설정하려면 자바스크립트 파일의 시작 부분에 'use strict';를 삽입하면 된다.

스트릭 모드를 사용하면 자바스크립트에 보다 엄격한 규칙을 적용할 수 있다.
엄격한 규칙 중에는 전역 객체의 값을 Window 객체 대신에 undefined로 설정하는 규칙이 있어서,
전역 범위로 정의된 this 키워드의 값도 undefined가 된다.

this 값을 수동으로 설정하고자 할 때는 .bind()를 사용할 수 있다.

```javascript
const myCar = {
  color: "red",
  logColor: function () {
    console.log(this.color);
  },
};

const unboundGetColor = myCar.logColor;
unboundGetColor(); // undefined

const boundGetColor = unboundGetColor.bind(myCar);
boundGetColor(); // red
```

this 키워드의 값을 설정하는 데 사용할 수 있는 또 다른 방법으로는 .call()과 .apply() 두 가지 방법이 있다.
두 메서드 모두 주어진 this의 값으로 함수를 호출한다는 점에서 비슷하지만, 받아들이는 인수가 약간 다르다.

.call()은 인수의 목록을 받는 반면
.apply()는 하나의 인수 배열을 받는다.

.call()을 사용하는 예제

```javascript
function Car(maker, color) {
  this.carMaker = maker;
  this.carColor = color;
}

function MyCar(maker, color) {
  Car.call(this, maker, color);
  this.age = 5;
}
const myNewCar = new MyCar("bmw", "red");
console.log(myNewCar.carMaker); // bmw
console.log(myNewCar.carColor); // red

console.log(myNewCar);
```

.call()에 MyCar 객체를 전달하여 this.carMaker가 MyCar의 인수로 전달한 maker로 설정되도록 했다.
color도 마찬가지로 처리했다.

.apply()를 사용한 예제

```javascript
function Car(maker, color) {
  this.carMaker = maker;
  this.carColor = color;
}

function MyCar(maker, color) {
  Car.apply(this, [maker, color]);
  this.age = 5;
}

const myNewCar = new MyCar("bmw", "red");
console.log(myNewCar.carMaker); // bmw
console.log(myNewCar.carColor); // red
```

결과는 동일하지만 .apply()는 인수 목록이 담긴 배열을 받는다.

함수에 필요한 인수의 수를 모르거나 알 필요가 없을 때에는 .apply()를 주로 쓰게 된다.
이런 경우에 .call()은 인수를 개별적으로 전달해야 하므로 사용할 수 없다.
.apply()는 배열을 전달할 수 있고, 배열에 포함된 원소의 수에 관계 없이 함수 내부로 전달할 수 있다.

```javascript
const ourFunction = function (item, method, args) {
  method.apply(args);
};

ourFunction(item, method, ["argument1", "argument2"]);
ourFunction(item, method, ["argument1", "argument2", "argument3"]);
```

전달하는 인수의 수에 관계없이 .apply()가 호출될 때 개별적으로 각 인수가 적용된다.
