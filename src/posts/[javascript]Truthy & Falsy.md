---
title: javascript 응용 - Truthy & Falsy
description: javascript 응용 - Truthy & Falsy
permalink: posts/{{ title | slug }}/index.html
date: "2022-02-14"
tags: [javascript, Truthy & Falsy]
---

## Truthy & Falsy

참 같은 값, 거짓 같은 값

```javascript

let a = "string";

if (a) {
  console.log("TRUE");
} else {
  console.log("FALSE");
}
=> console.log("TRUE");

let a = [];
if (a) {
  console.log("TRUE");
} else {
  console.log("FALSE");
}
=> console.log("TRUE");


let a = {};
if (a) {
  console.log("TRUE");
} else {
  console.log("FALSE");
}
=> console.log("TRUE");

let a = "";
if (a) {
  console.log("TRUE");
} else {
  console.log("FALSE");
}
=> console.log("FALSE");

let a = undefined;
if (a) {
  console.log("TRUE");
} else {
  console.log("FALSE");
}
=> console.log("FALSE");


let a = null;
if (a) {
  console.log("TRUE");
} else {
  console.log("FALSE");
}
=> console.log("FALSE");

let a = 0;
if (a) {
  console.log("TRUE");
} else {
  console.log("FALSE");
}
=> console.log("FALSE");

let a = NaN;
if (a) {
  console.log("TRUE");
} else {
  console.log("FALSE");
}
=> console.log("FALSE");

```

```javascript

const getName = (person) => {
  return person.name;
};
let person = { name: 'riverkim' };
const name = getName(person);


console.log(name); => "riverkim"


const getName = (person) => {
  if(person === undefined){
    return "객체가 아닙니다."
  }
  return person.name;
};

let person;

const name = getName(person);

console.log(name); => "객체가 아닙니다."


const getName = (person) => {
  if(person === undefined || person === null) {
    return "객체가 아닙니다."
  }
  return person.name;
};

let person;

const name = getName(person);

console.log(name); => "객체가 아닙니다."

// 예외처리
const getName = (person) => {
  if(!person) {
    return "객체가 아닙니다."
  }
  return person.name;
};

let person = null;

const name = getName(person);

console.log(name); => "객체가 아닙니다."



```
