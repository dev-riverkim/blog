---
title: javascript 응용 - spread 와 rest
description: javascript 응용 - spread 와 rest
permalink: posts/{{ title | slug }}/index.html
date: "2022-02-16"
tags: [javascript, spread, rest]
---

## spread 와 rest

### spread

spread 라는 단어가 가지고 있는 의미는 펼치다, 퍼뜨리다. 이 문법을 사용하면, 객체 혹은 배열을 펼칠 수 있다.

```javascript
const slime = {
  name: "슬라임",
};

const cuteSlime = {
  name: "슬라임",
  attribute: "cute",
};

const purpleCuteSlime = {
  name: "슬라임",
  attribute: "cute",
  color: "purple",
};

console.log(slime);
console.log(cuteSlime);
console.log(purpleCuteSlime);
```

기존의 것을 건드리지 않고 새로운 객체를 만들어 사용

이러한 상황에 사용 할 수 있는 유용한 문법이 spread

```javascript
const slime = {
  name: "슬라임",
};

const cuteSlime = {
  ...slime,
  attribute: "cute",
};

const purpleCuteSlime = {
  ...slime,
  ...cuteSlime,
  color: "purple",
};

console.log(slime);
console.log(cuteSlime);
console.log(purpleCuteSlime);
```

spread 연산자는 배열에서도 사용 가능

```javascript
const animals = ["개", "고양이", "참새"];
const anotherAnimals = [...animals, "비둘기"];

console.log(animals);
console.log(anotherAnimals);
```

배열에서 spread 연산자를 여러번 사용 할 수도 있습니다.

```javascript
const numbers = [1, 2, 3, 4, 5];

const spreadNumber = [...numbers, 10, 20, 40, ...numbers];

console.log(spreadNumbers);
```

### rest

rest는 생김새는 spread 랑 비슷한데, 역할이 매우 다르다.

rest는 객체, 배열, 그리고 함수의 파라미터에서 사용이 가능

```javascript
// 객체에서의 rest
const purpleCuteSlime = {
  name: "슬라임",
  attribute: "cute",
  color: "purple",
};

const { color, ...rest } = purpleCuteSlime;

console.log(color);
console.log(rest);
```

```javascript

```
