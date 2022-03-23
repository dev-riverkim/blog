---
title: chapter4 - 템플릿 리터럴
description: 모던자바스크립트 핵심가이드 정리
permalink: posts/{{ title | slug }}/index.html
date: "2022-03-23"
tags: [javascript, 템플릿 리터럴]
---

ES6 이전에는 템플릿 문자열이라고 부르던 것을 ES6에 와서는 템플릿 리터럴 이라고 부르게 되었다.

# 4.1 문자열 삽입

ES5에서는 문자열을 삽입하기 위한 코드를 다음과 같이 작성했다.

```javascript
var name = "riverkim";
var greeting = "hello my name is " + name;

console.log(greeting); // hello my name is riverkim
```

ES6에서는 백틱을 사용하여 코드를 더 쉽게 작성할 수 있게 되었다.

```javascript
let name = "riverkim";
const greeting = `hello my name is ${name}`;

console.log(greeting); // hello my name is riverkim
```

# 4.2 표현식 삽입

표현식을 삽입하려면 ES5에서는 다음 예시처럼 코드를 작성했다.

```javascript
var a = 1;
var b = 10;
console.log("1 * 10 is " + a * b); // 1 * 10 is 10
```

ES6에서는 백틱을 사용하여 타이핑을 줄일 수 있다.

```javascript
var a = 1;
var b = 10;
console.log(`1 * 10 is ${a * b}`); // 1 * 10 is 10
```

# 4.3 여러 줄 문자열 생성

ES5에서는 HTML 프래그먼트 등에 사용할 여러 줄로 이뤄진 문자열을 다음과 같이 구현했다.

```javascript
// 각 행마다 백슬래시를 삽입해야 함
var text = "hello,\n my name is Riverkim\n how are you? \n";

console.log(text);
```

ES6에서는 전체를 백틱으로 감싸기만 하면 된다.

```javascript
const content = `hello, 
my name is Riverkim 
how are you?`;

console.log(content);
```

# 4.4 중첩 템플릿

템플릿 안에 템플릿을 중첩하는 것도 가능

```javascript
const people = [
  { name: "Reverkim", age: 27 },
  { name: "Caroline", age: 27 },
  { name: "josh", age: 31 },
];

const markup = `<ul>${people.map((person) => `<li>${person.name}</li>`)}</ul>`;

console.log(markup); //<ul><li>Reverkim</li>,<li>Caroline</li>,<li>josh</li></ul>
```

map 함수를 사용하여 people의 각 원소에 대해 반복 동작을 수행하고 people 내에 있는 name을 담아 li 태그를 표시했다.

# 4.5 삼항 연산자 추가하기

삼항 연산자를 사용하면 템플릿 문자열 내에 로직을 쉽게 추가할 수 있다.

```javascript
const isDiscounted = false;
function getPrice() {
  console.log(isDiscounted ? "10$" : "20$");
}
getPrice(); // 20$
```

? 앞의 조건이 true이면 첫 번째 값이 반환되고, 그렇지 않으면 : 뒤에 있는 값이 반환된다.

```javascript
// name, age와 함께 artist를 생성

const artist = {
  name: "Bon JoVi",
  age: 56,
};

// artist 객체에 song 프로퍼티가 있을 때만 문장에 추가하고,
// 없으면 아무것도 반환하지 않음

const text = `
  <div>
    <p>${artist.name} is ${artist.age} years old ${
  artist.song ? `and wrote the song. ${artist.song}` : ""
}</p>
  </div>
`;

console.log(text);
// <div>
//   <p>Bon JoVi is 56 years old </p>
// </div>;

const artist2 = {
  name: "Trent Reznor",
  age: 53,
  song: "Hurt",
};

const text2 = `
  <div>
    <p>${artist2.name} is ${artist2.age} years old ${
  artist2.song ? `and wrote the song. ${artist2.song}` : ""
}</p>
  </div>
`;

console.log(text2);
// <div>
//   <p>Trent Reznor is 53 years old and wrote the song. Hurt</p>
// </div>;
```

# 4.6 템플릿 리터럴에 함수 전달하기

필요하다면 템플릿 리터럴 내에 함수를 전달할 수도 있다.

```javascript
const groceries = {
  meat: "port chop",
  veggie: "salad",
  fruit: "apple",
  others: ["mushrooms", "instant noodles", "instans soup"],
};

//groceries의 각 값에 대해 map을 수행하는 함수
function groceryList(others) {
  return `
  <p>
  ${others.map((other) => `<span>${other}</span>`).join("\n")}
  </p>
  `;
}

// p 태그 내 모든 groceries를 출력.
// 마지막은 **others** 배열의 모든 원소를 포함

const markup = `
<div>
<p>${groceries.meat}</p>
<p>${groceries.veggie}</p>
<p>${groceries.fruit}</p>
<p>${groceryList(groceries.others)}</p>

</div>
`;

console.log(markup);

// <div>
//   <p>port chop</p>
//   <p>salad</p>
//   <p>apple</p>
//   <p>
//     <p>
//       <span>mushrooms</span>
//       <span>instant noodles</span>
//       <span>instans soup</span>
//     </p>
//   </p>
// </div>;
```

마지막 p 태그에서 함수 groceryList를 호출하여 다른 모든 others 를 인수로 전달했다.

함수 내에서 p 태그를 반환하고 map을 사용하여 groceries의 각 원소에 대해 반복하여
각 원소를 담은 span 태그 배열을 반환한다.

그런다음 .join('\n')을 사용하여 각 span 뒤에 새 행을 추가했다.

# 4.7 태그된 템플릿 리터럴

함수를 태그하여 템플릿 리터럴을 실행하면 템플릿 내부에 있는 모든 항목이 태그된 함수의 인수로 제공된다.

작동 방식은 매우 간단하다. 함수 이름을 가져다 실행할 템플릿 앞에 쓰기만 하면 된다.

```javascript
let person = "Riverkim";
let age = 35;

function myTag(strings, personName, personAge) {
  // strings: ["That","is a", "!"]
  let str = strings[1]; // is a
  let ageStr;

  personAge > 50 ? (ageStr = "grandpa") : (ageStr = "youngster");

  return personName + str + ageStr;
}

let sentence = myTag`That ${person} is a ${age}!`;
console.log(sentence); // Riverkim is a youngster
```

이 코드의 함수는 age 변수의 값을 받아서 삼항 연산자를 사용하여 출력할 항목을 결정한다.
함수에서 첫 번째 인수 strings는 let sentence 문의 전체 문자열 중 템플릿 리터럴 변수를 제외한
문자열들이 담긴 배열로 설정되고, 템플릿 리터럴 변수들이 나머지 인수가 된다.

strings 배열의 각 원소는 템플릿 리터럴에 포함된 변수들을 구준자로 삼아 문자열을 나눈 결과와 같다.
이 예에서 문자열은 That, ${person}, is a, ${age},! 다섯 부분으로 나뉘므로
여기서 변수를 제외한 ["That","is a", "!"] 가 strings가 된다.

배열 표기법을 사용하여 다음과 같이 중간에 있는 문자열에 접근할 수 있다.

```javascript
let str = strings[1]; // is a
```
