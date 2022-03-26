---
title: algorithm - 자바스크립트 100제 - 21 ~ 30
description: javascript 응용 - 삼항연산자
permalink: posts/{{ title | slug }}/index.html
date: "2022-03-26"
tags: [javascript, algorithm]
---

# Chapter 1-3

## 문제21 - set은 어떻게 만드나요?

다음 중 set을 만드는 방법으로 올바른 것을 모두 고르시오.

3.  var x = new Set('javascript');
4.  var x = new Set();

## 문제22 : 배수인지 확인하기

다음 중 변수 i가 6의 배수인지 확인하는 방법으로 올바른 것은?

2.  i % 6 == 0

## 문제23 : OX문제

console.log(10/3)의 출력 결과는 3이다.

X

정답은 'X'입니다.
출력 결과는 3.3333333333333335 이 나옵니다.
소숫점이 없는 정수를 출력하고자 할 때는 Math.floor() 함수를 쓰면 됩니다.

## 문제24 : 대문자로 바꿔주세요!

민지는 국제 포럼에서 아르바이트를 하게 되었습니다.
민지는 각 국에서 온 참가자들의 명단을 엑셀로 정리하고 있는데
참가자들 이름이 어떤 이는 전부 소문자, 어떤 이는 전부 대문자로 써져 있는 등 형식이 제각각이었습니다.

민지를 위해 이름이 입력되면 전부 대문자로 출력되는 프로그램을 만들어주세요.

```javascript
// 입출력

// 입력 : mary
// 출력 : MARY

const name = prompt("이름을 입력해주세요.");

const result = name.toUpperCase();

console.log(result);
```

## 문제25 : 원의 넓이를 구하세요

원의 넓이는 반지름의 길이 x 반지름의 길이 x 3.14로 구할 수 있습니다.
함수를 사용하여 원의 넓이를 구하는 코드를 작성해봅시다.

입력으로 반지름의 길이 정수 n이 주어지면 원의 넓이를 반환하는 함수를 만들어 주세요.

```javascript
// const n = prompt("반지름의 길이를 입력해 주세요.");

// const result = n * n * 3.14;

// console.log(result);

const number = prompt("반지름의 길이를 입력해주세요");

function circleWidth(number) {
  return number * number * 3.14;
}

const result = circleWidth(number);

console.log(result);

// function circle(n) {
//   const result = n * n * 3.14;

//   return result;
// }

// const r = prompt("원의 반지름을 입력하세요.");

// console.log(circle(r));
```

## 문제26 : 행성 문제2

우리 태양계를 이루는 행성은 수성, 금성, 지구, 화성, 목성, 토성, 천왕성, 해왕성이 있습니다.
이 행성들의 영어 이름은 Mercury, Venus, Earth, Mars, Jupiter, Saturn, Uranus, Neptune입니다.

행성의 한글 이름을 입력하면 영어 이름을 반환하는 프로그램을 만들어 주세요.

```javascript
const arr1 = [
  "수성",
  "금성",
  "지구",
  "화성",
  "목성",
  "토성",
  "천왕성",
  "해왕성",
];

const arr2 = [
  "Mercury",
  "Venus",
  "Earth",
  "Mars",
  "Jupiter",
  "Saturn",
  "Uranus",
  "Neptune",
];

const planet = prompt("행성 이름을 입력해주세요.");

for (i = 0; i < arr1.length; i++) {
  if (arr1[i] === planet) {
    console.log(arr2[i]);
  }
}

// const planets = {
// 	'수성' : 'Mercury',
// 	'금성' : 'Venus',
// 	'지구' : 'Earth',
// 	'화성' : 'Mars',
// 	'목성' : 'Jupiter',
// 	'토성' : 'Saturn',
// 	'천왕성' : 'Uranus',
// 	'해왕성' : 'Neptune',
// };

// const name = prompt("행성의 이름을 입력하세요.");

// console.log(planets[name]);
```

## 문제27 : 객체 만들기

첫번째 입력에서는 학생의 이름이 공백으로 구분되어 입력되고, 두번째에는 그 학생의 수학 점수가 공백으로 구분되어 주어집니다.

두 개를 합쳐 학생의 이름이 key이고 value가 수학 점수인 객체를 출력해주세요.

```javascript
// 입력
// Yujin Hyewon
// 70 100

// 출력
// {'Yujin': 70, 'Hyewon': 100}

const studentName = prompt("학생의 이름을 입력해 주세요").split(" ");

const studentScore = prompt("학생의 점수를 입력해 주세요").split(" ");

const obj = {};

for (i = 0; i < studentName.length; i++) {
  obj[studentName[i]] = studentScore[i];
}

console.log(obj);

// const keys = prompt('이름을 입력하세요').split(' ');
// const values = prompt('점수를 입력하세요').split(' ');
// const obj = {};

// for (let i=0; i<keys.length; i++) {
//   obj[keys[i]] = parseInt(values[i], 10);
// }

// console.log(obj);
```

## 문제28 : 2-gram

2-gram이란 문자열에서 2개의 연속된 요소를 출력하는 방법입니다.

예를 들어 'Javascript'를 2-gram으로 반복해 본다면 다음과 같은 결과가 나옵니다.
입력으로 문자열이 주어지면 2-gram으로 출력하는 프로그램을 작성해 주세요.

```javascript
const data = prompt("문자를 입력하세요.");

for (let i = 0; i < data.length - 1; i++) {
  console.log(data[i], data[i + 1]);
}
```

## 문제29 : 대문자만 지나가세요

진구는 영어 학원 아르바이트를 하고 있습니다. 반 아이들은 알파벳을 공부하는 학생들인데 오늘은 대문자 쓰기 시험을 봤습니다.

알파벳 하나만을 입력하고 그 알파벳이 대문자이면 YES를 아니면 NO를 출력하는 프로그램을 만들어 주세요.

```javascript
const alphabet = prompt("알파벳을 입력해주세요.");

function isUpperCase(alphabet) {
  if (alphabet === alphabet.toUpperCase()) {
    return console.log("YES");
  } else {
    return console.log("NO");
  }
}

isUpperCase(alphabet);

// const data = prompt('알파벳을 입력하세요.');

// if (data === data.toUpperCase()){
//   console.log('YES');
// } else {
//   console.log('NO');
// }
```

## 문제30 : 문자열 속 문자 찾기

문자 pineapple에는 apple이라는 문자가 숨어 있습니다. 원범이는 이렇듯 문자열 속에 숨어있는 문자를 찾아보려고 합니다.

첫번째 입력에서는 문자열이 입력되고, 두번째에는 찾을 문자가 입력되어야 합니다.
그 문자가 시작하는 index를 반환하는 프로그램을 만들어 주세요

```javascript
// 입력
// pineapple is yummy
// apple

// 출력
// 4

const text = prompt("문장을 입력해 주세요");
const findWord = prompt("찾을 문장을 입력해 주세요");

const result = text.indexOf(findWord);
console.log(result);

// const data = prompt("문자열을 입력하세요");
// const word = prompt("찾을 단어를 입력하세요");

// console.log(data.indexOf(word));
/* indexOf() 메서드는 호출한 스트링 객체나 배열에서
 * 주어진 값과 일치하는 값 혹은 요소의 첫 번째 인덱스를 반환하고 존재하지 않으면 -1을 반환합니다.
 */
```
