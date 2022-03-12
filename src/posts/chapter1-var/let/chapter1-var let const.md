---
title: chapter1 - var,let,const
description: 모던자바스크립트 핵심가이드 정리
permalink: posts/{{ title | slug }}/index.html
date: "2022-03-12"
tags: [javascript]
---

ES6부터 let과 const가 도입되었고, 필요에 맞게 변수를 정의하는 것이 더 용이해 졌다.

# 1.1 var, let, const의 차이

## var

var 키워드로 선언된 변수는 함수 스코프에 종속된다.
반면, for 루프(블록 스코프) 내에서 var 키워드로 변수를 선언하면 이 변수를 for루프 밖에서도 사용할 수 있다.
