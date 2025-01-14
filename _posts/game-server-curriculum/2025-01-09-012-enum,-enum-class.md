---
title: (12) enum, enum class
excerpt: enum 과 enum class에 대해서 알아보자
categories: 
  - 게임서버 과정
permalink: /game-server-curriculum/:title
toc: true
toc_sticky: true
typora-root-url: ../../
---

[toc]

## enum 이란

- 상수인데 열거형 상수라고 합니다.
- 특정 속성의 값을 제한하는 용도로 사용할 수 있습니다.
- C에서 enum은 타입 세이프하지 않습니다.

### C++에서 enum

- int 자료형에서 enum 형으로의 암묵적 캐스팅이 허용되지 않습니다.
- 서로 다른 이름의 enum 에 동일한 속성 명이 존재하면 이름 충돌이 발생한다.
- enum 변수에서 int 형 변수로 묵시적 캐스팅이 허용됩니다.

### C++ 11 에서 생긴 enum class

- enum class 에서 int, int 에서 enum class 로의 묵시적 캐스팅을 허용하지 않습니다.
- 서로 다른 이름의 enum 에 동일한 속성 명이 존재하여도 이름 충돌이 발생하지 않습니다. 속성 명의 유효성 검사 범위를 enum class 내부로 한정합니다.

### enum class 활용법

- 함수 인자로 일반 int형 대신 enum class 형식을 사용하는 것이 프로그래머의 실수를 줄이는 좋은 방법이며, 타입 세이프합니다.
