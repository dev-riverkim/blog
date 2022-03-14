---
title: algorithm - 자바스크립트 100제
description: javascript 응용 - 삼항연산자
permalink: posts/{{ title | slug }}/index.html
date: "2022-02-16"
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

var result = //빈칸을 채워주세요

console.log(result);


출력
2019/04/26 11:34:27
```
