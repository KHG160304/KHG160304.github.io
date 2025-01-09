---
title: (11) #define과-typedef
excerpt: #define과 typedef의 특징 및 차이점에 대해서 알아보자
categories: 
  - 게임서버 과정
permalink: /game-server-curriculum/:title
toc: true
toc_sticky: true
typora-root-url: ../../
---

[toc]

## #define

- 일반적으로 숫자 또는 문자열 상수 값에 별칭을 붙여서, 코드에 상수 값을 사용하는 대신 별칭으로 사용하면 코드 작성하기도 쉽고 가독성도 높이려는 목적으로 사용합니다.
- #define 키워드는 전처리기에서 처리합니다.

### 동작 원리

1. 소스코드를 컴파일하기 전에 전치리기가 먼저 #define으로 정의된 별칭들이 코드에 존재하는지 탐색합니다.
2. 발견한 별칭들은 모두 별칭이 지칭한 값으로 치환됩니다. 
3. 실제 컴파일되는 소스코드에는 별칭을 대신하여 실제 값이 들어가 있는 것을 볼 수 있습니다.

> 단순히 별칭을 실제 값으로 바꿔치기 한다고 생각하면 됩니다. 

~~~cpp
#define PI 3.14
#define SQUARE(x) x*x
#include <stdio.h>

int main(void) 
{
    printf("%d\n", PI);
    // printf("%d\n", 3.14);
    // 전처리기가 전처리를 한 이후 소스코드에서 PI는 모두 사라지고 3.14로 치환됩니다.
    printf("%d\n", SQUARE(3)); 
    // printf("%d\n", 3*3);
    // 전처리기가 전처리를 한 이후 소스코드에서 SQUARE(3)은 모두 사라지고 3*3 으로 치환됩니다.
    // 전처리 후에 컴파일러가 변경된 소스코드를 컴파일 합니다.
    return 0;
}
~~~

### #define 단점

1. 타입 검증이 되지 않습니다.
2. 매번 코드가 복사되기 때문에 실행 코드가 늘어납니다.
3. pre-processor에서 처리되기 때문에 컴파일러에서 제어할 수 없습니다.

## typedef

- 특정 자료형에 별칭을 붙여서, 코드상에서 해당 별칭을 사용하고 싶을 때 typedef 키워드를 활용하면 새로운 별칭을 부여할 수 있습니다.
- typedef로 정의한 별칭에 또 typedef를 활용해서 별칭을 붙일 수 있습니다.
- typedef 키워드는 컴파일러가 처리합니다.

~~~ cpp
typedef int SOCKET;
typedef struct CREDIT_CARD
{
    int card_id;
    int date;
    int username;
} CREDIT_CARD;

int main(void)
{
    //socket 값에 사용하는 실제 데이터 타입은 int 이지만, SOCKET이라고 별칭을 붙이면, 특정 데이터가 어떤 자료형을 사용하는지 고민할 필요없이 별칭으로 코드를 작성하면, 컴파일러가 알아서 자료형을 int로 바꿔서 사용한다. 별칭을 사용하는게 가독성도 좋고 기억하기도 쉽습니다.
    SOCKET i = 0;
    CREDIT_CARD = { 0 };
    return 0;
}
~~~



### WIN API에서 typedef 활용법

- unsigned char는 BYTE, unsigned short는 WORD, unsigned int는 DWORD로 재정의 한다. 

- 재정의하는 이유는 어떤 언어를 사용해도 동일하게 실행되야 한다. 

- WIN API는 언어 중립적이어야 한다. 

- 통일된 이름의 자료형을 사용하기 위해서 특정언어에 종속된 자료형이 아닌 재정의한 자료형 명을 사용합니다.
