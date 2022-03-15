---
title: algorithm - 자바스크립트 100제
description: javascript 응용 - 삼항연산자
permalink: posts/{{ title | slug }}/index.html
date: "2022-03-14"
tags: [javascript, algorithm]
---

# Chapter 1-1

## 문제1 - 배열의 삭제

다음 배열에서 400, 500를 삭제하는 code를 입력하세요.

```javascript
var nums = [100, 200, 300, 400, 500];
nums.pop();
nums.pop();
console.log(nums); // [100, 200, 300]
```

## 문제2 - 배열의 내장함수(splice)

<pass>부분에 배열 내장함수를 이용하여 코드를 입력하고 다음과 같이 출력되게 하세요.

```javascript
var arr = [200, 100, 300];
//pass
arr.splice(2, 0, 10000);
console.log(arr);

출력[(200, 100, 10000, 300)];
```

## 문제3 - 변수의 타입

다음 출력 값으로 올바른 것은?

```javascript
var arr = [100, 200, 300];
console.log(typeof arr);
```

4. object

## 문제4 - 변수의 타입2

다음 변수 a를 typeof(a)로 넣었을 때 출력될 값과의 연결이 알맞지 않은 것은?

2.  입력 : a = 2.22, 출력 : boolean

## 문제5 : for문 계산

다음 코드의 출력 값으로 알맞은 것은?

```javascript
var a = 10;
var b = 2;

for (var i = 1; i < 5; i += 2) {
  a += i;
}

console.log(a + b);
```

4.  16
    i 값이 1부터 시작하고 한번 순환할 때마다 2씩 증가하기 때문에 for 문은 총 두 번 순환합니다.

## 문제6 : False

다음은 자바스크립트 문법 중에서 False로 취급하는 것들 입니다.
앗, False로 취급하지 않는 것이 하나 있네요! True를 찾아주세요.

2.  1

## 문제7 : 변수명

다음 중 변수명으로 사용할 수 없는 것 2개를 고르시오.

3.  let
4.  1age

정답은 '3번', '5번' 입니다. JavaScript 식별자는 문자, 밑줄(\_) 혹은 달러 기호($)로 시작해야하며 let 은 이미 JavaScript 문법에 존재하는 예약어라 사용이 불가능합니다.

## 문제8 : 객체의 키 이름 중복

자바스크립트 객체를 다음과 같이 만들었다.
출력값을 입력하시오. (출력값은 공백을 넣지 않습니다. )

```javascript
var d = {
  height: 180,
  weight: 78,
  weight: 84,
  temperature: 36,
  eyesight: 1,
};

console.log(d["weight"]);
```

정답은 '84' 입니다.

## 문제9 : concat을 활용한 출력 방법

다음 소스 코드를 완성하여 날짜와 시간을 출력하시오.

```javascript
데이터
var year = '2019';
var month = '04';
var day = '26';
var hour = '11';
var minute = '34';
var second = '27';

var result = year.concat("/",month,"/",day, " ", hour,":",minute,":",second)

console.log(result);
//concat() 메서드는 매개변수로 전달된 문자열을 메서드를 호출한 문자열에 붙여 새로운 문자열로 반환합니다.

출력
2019/04/26 11:34:27

```

## 문제10 : 별 찍기

크리스마스 날, 은비는 친구들과 함께 파티를 하기로 했습니다. 그런데, 크리스마스 트리를 사는 것을 깜빡하고 말았습니다. 온 가게를 돌아다녀 봤지만 크리스마스 트리는 모두 품절이었습니다.
하는 수 없이 은비는 프로그래밍으로 트리를 만들기로 합니다.

은비를 위해 프로그램을 작성해 주세요.

```javascript
입력
5

출력
    *        1
   ***       3
  *****      5
 *******     7
*********    9

const n = prompt('숫자를 입력하세요.');
let tree = '';

for(let i=1; i<=n; i++){
  let star = '';
  for(let j=1; j<=n-i; j++){
    star += ' ';
  }
  for(let k=1; k<=2*i-1; k++){
    star += '*';
  }
  tree += star + '\n';
}

console.log(tree);


```

## 문제11 : for를 이용한 기본 활용

1부터 100까지 모두 더하는 Code를 <pass> 부분에 완성하세요. for를 사용해야 합니다.

```javascript
let s = 0;

//pass

let s = 0;
for (i = 1; i <= 100; i++) {
  s += i;
}

console.log(s);
```

## 문제12 : 게임 캐릭터 클래스 만들기

다음 소스코드에서 클래스를 작성하여 게임 캐릭터의 능력치와 '파이어볼'이 출력되게 만드시오.
주어진 소스 코드를 수정해선 안됩니다.

```javascript
// 데이터
// <여기에 class를 작성하세요.>

// const x = new Wizard(545, 210, 10);
// console.log(x.health, x.mana, x.armor);
// x.attack();

// 출력
// 545 210 10
// 파이어볼

const Wizard = class Wizard {
  constructor(health, mana, armor) {
    this.health = health;
    this.mana = mana;
    this.armor = armor;
  }
  attack() {
    console.log("파이어볼");
  }
};

// function Wizard(health, mana, armor) {
//   this.health = health;
//   this.mana = mana;
//   this.armor = armor;
//   this.attack = function () {
//     console.log("파이어볼");
//   };
// }

const x = new Wizard(545, 210, 10);
console.log(x.health, x.mana, x.armor);
x.attack();
```

## 문제13 : 몇 번째 행성인가요?

우리 태양계를 이루고 있는 행성은 수성, 금성, 지구, 화성, 목성, 토성, 천왕성, 해왕성으로 총 8개 입니다. 저희는 우리 태양계의 n번째 행성이 무엇인지 알고 싶습니다.

입력으로 행성의 순서를 나타내는 숫자 n이 입력됩니다.
출력으로 그 순서에 해당하는 행성의 이름을 출력해 주세요.

예를들어 1이 입력되면, 첫번째 행성인 수성이 출력됩니다.

```javascript
// 입출력;

// 입력: 1;
// 출력: 수성;

const solarSystem = [
  "수성",
  "금성",
  "지구",
  "화성",
  "목성",
  "토성",
  "천왕성",
  "해왕성",
];

let inputValue = prompt("몇 번째 행성을 찾고 싶은가요?");

console.log(solarSystem[inputValue - 1]);
```

## 문제14 : 3의 배수 인가요?

영희는 친구와 게임을 하고 있습니다. 서로 돌아가며 랜덤으로 숫자를 하나 말하고 그게 3의 배수이면 박수를 치고 아니면 그 숫자를 그대로 말하는 게임입니다.

입력으로 랜덤한 숫자 n이 주어집니다.

만약 그 수가 3의 배수라면 '짝'이라는 글자를, 3의 배수가 아니라면 n을 그대로 출력해 주세요.

```javascript
// 입출력

// 입력 : 3
// 출력 : 짝

// 입력 : 2
// 출력 : 2

let n = prompt("숫자를 입력해주세요!");

if (n % 3 === 0) {
  console.log("짝");
} else {
  console.log(n);
}
```

## 문제15 : 자기소개

신학기가 시작되고, 아이들이 돌아가면서 자기소개를 하기로 했습니다.

만약 입력으로 김다정이라는 이름이 주어지면 "안녕하세요. 저는 김다정입니다."라고 출력하게
해주세요.

```javascript
// 입출력

// 입력 : 김다정
// 출력 : 안녕하세요. 저는 김다정입니다.
let name = prompt("이름을 입력해 주세요");

function sayHello(name) {
  console.log("안녕하세요. 저는 " + name + "입니다.");
}
sayHello(name);

const name = prompt("이름을 입력하세요.");

console.log(`안녕하세요. 저는 ${name}입니다.`);
/*
 * es6부터는 backtick 문자열(``) 안에서 $와 중괄호로 표현식을 사용할 수 있습니다.
 * 이를 템플릿 리터럴(Template literals)이라 합니다.
 */
```

## 문제16 : 로꾸거

문장이 입력되면 거꾸로 출력하는 프로그램을 만들어 봅시다.
