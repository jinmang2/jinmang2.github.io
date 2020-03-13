---
title: "C언어 Pointer란 무엇인가?"
date: 2020-03-14 00:19:00 -0400
categories: C
---

# 혼자 공부하는 C언어, **Pointer**
- C 언어로 시스템 프로그래밍이 가능한 것은 포인터가 있기 때문
- 포인터는 어렵지 않음, 단지 헷갈릴 뿐! (그게 어려운거다 멍청아!)
- 따라서 포인터의 의미를 이해한다면 응용도 어렵지 않음 (그건 맞음)
- 이번 포스팅에서는 포인터의 개념을 잡아주고 기본적인 사용법을 설명!

## 1. 포인터의 기본 개념
- 변수 선언 > 메모리에 공간 확보
- 변수명: 메모리 공간을 식별할 수 있는 이름
- 그러나, 변수는 선언된 블록({}), 함수 내부로 사용이 제한
- 때문에 사용 범위를 벗어난 경우도 데이터를 공유할 수 있는 새로운 방법이 필요!
- 그것이 바로 포인터!

### 메모리의 주소
- 프로그램이 사용하는 메모리의 위치는 **주소 값**으로 식별이 가능
- `int a;` 선언 (int이기 때문에 4bytes만큼 메모리 공간이 잡힘)

    ![pointer1](https://user-images.githubusercontent.com/37775784/76636230-0ad85d00-658c-11ea-92cc-b78700c1ed28.png)
    
### 주소 연산자: `&`
- 저장된 공간을 이름이 아닌 주소로 사용해보자!
- `주소`: 변수가 할당된 메모리 공간의 시작 주소

```c
// 변수의 메모리 주소 확인
#include <stdio.h>

int main(void){
    int a;
    double b;
    char c;
    
    printf("   int형 변수의 주소 = 10진수: %u, 16진수: %p\n", &a, &a);
    printf("double형 변수의 주소 = 10진수: %u, 16진수: %p\n", &b, &b);
    printf("  char형 변수의 주소 = 10진수: %u, 16진수: %p\n", &c, &c);
        
    return 0;
}
```

```
   int형 변수의 주소 = 10진수: 8256220, 16진수: 007DFADC
double형 변수의 주소 = 10진수: 8256204, 16진수: 007DFACC
  char형 변수의 주소 = 10진수: 8256195, 16진수: 007DFAC3
```

- 주소 연산자로 아래와 같이 변수에 할당된 메모리의 시작 주소를 확인하고 변수의 크기를 더하여 메모리 어디에 할당되었는지 알 수 있음
- 주소는 16진수로 표기함. 어지간해서는 `%p`로 확인하자

    ![pointer2](https://user-images.githubusercontent.com/37775784/76637309-d8c7fa80-658d-11ea-90b5-21394175028e.png)

### 포인터와 간접 참조 연산자: `*`
- 포인터: 변수의 메모리 주소를 저장하는 변수
- 선언은 `*`를 붙여서!

```c
// 포인터의 선언과 사용
#include <stdio.h>

int main(void){
    
    int a;      // 일반 변수 선언
    int *pa;    // 포인터 선언
    
    pa = &a;    // 포인터에 a의 주소 대입
                // a의 주소 값의 `시작` 값이 저장!! 왜 시작이냐?
                // 변수의 크기만 알면 얼마나 메모리 공간이 할당되었는지
                // 알 수 있자나~
                // 너의 맘도 알고싶다 뭔 생각하는지
                // 말 안해주면 내가 어떻게 알아
    *pa = 10;   // 포인터로 변수 a에 10 대입
                // 이것이 바로 unary-indirection operation
    
    printf("  포인터로 a 값 출력 : %d\n", *pa);
    printf("변수명으로 a 값 출력 : %d\n", a);
    
    return 0;
}
```

```
  포인터로 a 값 출력 : 10
변수명으로 a 값 출력 : 10
```

- 포인터 pa는 변수 a가 메모리 어디에 할당되었는지 그 위치를 기억
- 포인터가 어떤 변수를 가리키면 포인터로 가리키는 변수를 사용할 수 있음
- 즉, 포인터로 변수를 사용할 수 있음!
- 위의 기능으로 사용할 때 특별한 연산자를 사용하는 데 이를
- `unary-indirection operators`, **간접 참조 연산자**(*)라고 함
- *pa는 아래와 같이 생각 가능!

    ```c
    pa = &a     // pa가 a를 가리킴
    *pa = 10    // *pa로 a를 활용,
                // a의 left-value(저장 공간)에 10을 right-value(변수의 값)으로 저장
    ```
    
- Note that: `*pa == a; pa == &a`

### 여러 가지 포인터 사용해보기

```c
// 포인터를 사용한 두 정수의 합과 평균 계산
#include <stdio.h>

int main(void){
    int a = 10, b = 15, total;      // Declare variable and Initialize
    double avg;                     // Declare variable stored average
    int *pa, *pb;                   // Declare pointer
    int *pt = &total;               // Declare pointer and Initialize
    double *pg = &avg;              // Declare double type pointer and Initialize
    
    pa = &a;                        // Assign address of a to pa
    pb = &b;                        // Assign address of b to pb
    
    *pt = *pa + *pb;                // Add a and b using unary-indirection operator
    *pg = *pt / 2.0;                // Calc avergage using unary-indirection operator
    
    printf("두 정수의 값   : %d, %d\n", *pa, *pb);
    printf("두 정수의 합   : %d\n", *pt);
    printf("두 정수의 평균 : %.1lf\n", *pg);
    
    return 0;
}
```

```
두 정수의 값   : 10, 15
두 정수의 합   : 25
두 정수의 평균 : 12.5
```

### `const`를 사용한 포인터
- 예제 생략,
- 포인터에 사용된 `const`의 의미는?
- **pa가 가리키는 변수 a는 pa를 간접 참조하여 바꿀 수 없다!!**

    ```c
    ...
    int a = 10;
    const pa = &a;
    
    a = 20;     // 먹힌다.
    *pa = 20;   // 에러 발생. 왜? 포인터를 선언할 때 const로 상수화했기 때문에!!
    >>> error C2166: l-value가 const 개체를 지정합니다.
    ```
    
## 2. 포인터 완전 정복을 위한 포인터 이해하기
- 포인터는 주소를 저장하는 일정한 크기의 메모리 공간, 언제든지 다른 주소를 저장하거나 포인터끼리 대입 가능
- 그러나 일반 변수와는 달리 대입 연산에 엄격한 기준이 적용됨

### 주소와 포인터의 차이
- `주소`: 변수에 할당된 메모리 저장 공간의 시작 주소 값 자체
- `포인터`: 그 값을 저장하는 또 다른 메모리 공간
- 즉, 상수와 변수 차이!!!

```c
int a, b;
int *p;
// &a와 &b는 상수
// p는 변수!
p = &a;
p = &b;
```

![pointer3](https://user-images.githubusercontent.com/37775784/76639625-cc45a100-6591-11ea-935c-3fe2fbdb6950.png)

```c
int a;
int *pa, *pb;
pa = pb = &a;
```

![pointer4](https://user-images.githubusercontent.com/37775784/76639773-19c20e00-6592-11ea-9c40-e5312e4510fa.png)


### 주소와 포인터의 크기
- 포인터는 저장 공간. 즉, 크기가 존재
- 포인터의 크기는 컴파일러에 따라 다를 수 있음
- 그러나, **모든 주소와 포인터는 가리키는 자료형과 상관없이 그 크기가 같음**

```c
// 주소와 포인터의 크기
#include <stdio.h>

int main(void){
    char ch;
    int in;
    double db;
    
    char *pc = &ch;
    int *pi = &in;
    double *pd = &db;
    
    printf("   char 형 변수의 주소 크기 : %d\n", sizeof(&ch));
    printf("    int 형 변수의 주소 크기 : %d\n", sizeof(&in));
    printf(" double 형 변수의 주소 크기 : %d\n", sizeof(&db));
    
    
    printf("   char * 포인터의 주소 크기 : %d\n", sizeof(pc));
    printf("    int * 포인터의 주소 크기 : %d\n", sizeof(pi));
    printf(" double * 포인터의 주소 크기 : %d\n", sizeof(pd));
    
    
    printf("   char * 포인터가 가리키는 변수의 크기 : %d\n", sizeof(*pc));
    printf("    int * 포인터가 가리키는 변수의 크기 : %d\n", sizeof(*pi));
    printf(" double * 포인터가 가리키는 변수의 크기 : %d\n", sizeof(*pd));
    
    return 0;
}
```

```
   char 형 변수의 주소 크기 : 4
    int 형 변수의 주소 크기 : 4
 double 형 변수의 주소 크기 : 4
   char * 포인터의 크기 : 4
    int * 포인터의 크기 : 4
 double * 포인터의 크기 : 4
   char * 포인터가 가리키는 변수의 크기 : 1
    int * 포인터가 가리키는 변수의 크기 : 4
 double * 포인터가 가리키는 변수의 크기 : 8
```

![pointer5](https://user-images.githubusercontent.com/37775784/76640503-65c18280-6593-11ea-9d5e-9c0fc2a72c3b.png)

### 포인터의 대입 규칙

#### [규칙 1] 포인터는 가리키는 변수의 형태가 같을 때만 대입해야 함

```c
// 허용하지 않는 포인터의 대입
#include <stdio.h>

int main(void){
    int a = 10;
    int *p = &a;            // int pointer p 선언 및 a의 주소 값으로 초기화
    double *pd;             // double pointer pd 선언
    
    pd = p;                 // 포인터 p의 값을 포인터 pd에 대입
                            // 포인터의 크기는 같지만, 호환되는 타입이 다름!
    printf("%lf\n", *pd);   // 한번 찍어보세나 젊은이.
                            // 보고싶다.
    
    return 0;
}
```

```
-92559592117432108000000000000000000000000000000000000000000000.0000
// 보통은 아래의 경고 메세지 발생
warning C4133: '=' : 'int *'과(와) 'double *' 사이의 형식이 호환되지 않습니다.
```

![pointer7](https://user-images.githubusercontent.com/37775784/76641792-7ffc6000-6595-11ea-8ce0-40d1568f831d.png)

- 컴파일러는 p에 저장된 값을 int형 변수의 주소로 생각하고, pd에 저장된 값을 double형 변수의 주소로 생각
- pd에 p를 대입한 후에 간접 참조 연산을 수행하면 변수 a에 할당된 영역 이후의 할당되지 않은 영역까지 사용하게 됨


#### [규칙 2] 형 변환을 사용한 포인터의 대입은 언제나 가능함

```c
double a = 3.4;     // double형 변수 선언
double *pd = &a;    // pd가 double형 변수 a를 가리키도록 초기화
int *pi;            // int형 변수를 가리키는 포인터 선언
pi = (int *)pd;     // pd값을 형 변환하여 pi에 대입
```

![pointer8](https://user-images.githubusercontent.com/37775784/76641787-7d9a0600-6595-11ea-8853-8b2f5b52f518.png)

- 에러는 안뜨지만 8bytes가 아닌 앞의 4bytes만 사용 가능...

#### 여기서 잠깐! 알고 가라!
- 포인터는 항상 정상적으로 할당받은 메모리 공간의 주소를 저장해서 사용해라!
- 포인터 초기화를 항상 유념하라!
    - 이를 수행하지 않고 간접 참조 연산을 수행하면 알 수 없는 곳으로 찾아가 데이터를 바꾸게 된다!
    
### 포인터를 사용하는 이유
- 메모리에 직접 접근하는 경우
- 동적 할당한 메모리를 사용하는 경우
