---
title: "[Java] 3주차. 자바가 제공하는 다양한 연산자"
categories: Java
tags:
  - Java
  - Programming
  - coding
toc: true
toc_sticky: true
date: 2024-05-02
last_modified_at: 2024-05-02
---

![java.png](/assets/images/java.png)

# **자바가 제공하는 다양한 연산자**

프로그램에서 데이터를 처리하고 결과를 산출하는 것을 연산(operations)라고 한다. 연산에 사용되는 기호를 연산자(operator)라고 하고, 연산되는 데이터는 피연산자(operand)라고 한다. 연산자와 피연산자를 이용하여 연산의과정을 기술한 것을 연산식(expressions)라고 부른다

# 연산자의 종류

|  연산자의 종류  |                    연산자                    | 피연산자수 |                의미                 |
|:---------:|:-----------------------------------------:|:-----:|:---------------------------------:|
|    증감     |                  ++, --                   |  단항   |          데이터를 1혹은 -1씩 증감          |
|    산술     |               +, -, *, /, %               |  이항   |             사칙연산, 나머지             |
|    시프트    |                  <<, >>                   |  이항   |          해당 데이터를 시프트 연산           |
|  비교(관계)   |           <, >, >=, <=, ==, !=            |  이항   |      데이터와 데이터의 크기와 같은 값인지 비교      |
|    논리     |               &&, II, ^, ~                |  이항   |      데이터의 비트가 같은지(값이 같은지) 비교      |
|    조건     |              ?, : -> 조건? A:B              |  삼항   |      조건이 참, 거짓에 따라 다른 값을 선택       |
|    대입     | =, *=, /=, -=, &=, ^=, I=, <<=,<br/> >>=, >>>= |  이항   | 대입 연산자 우측의 값을 데이터와 연산후 데이터에 다시 대입 |

- 연산자는 변수의 값을 변경하거나 대입하는데 사용된다
- 자바에서는 연산자에 따라 연산 대상이 될 수 있는 데이터 타입이 정해져 있다 (정수나 실수만 가능)
- 오버플로 (overflow) 또는 언더플로 (underflow) 등 범위를 벗어나는 연산들에 대해서는 연산 결과에 불필요한 값이 저장된다
- 0으로 나눌 경우는 오류가 발생한다

---

## 1. 산술 연산자 (+, -, *, /, %)

자바에서 산술 연산자란 덧셈, 뺄셈, 곱셈, 몫, 나머지를 구하는 5가지의 연산자로 나누어진다

| 기호 |   설명    |      기능      |
|:--:|:-------:|:------------:|
| +  | 덧셈 / 부호 | 3 + 4, a + b |
| -  | 뺄셈 / 부호 | 3 - 4, a - b |
| *  |   곱셈    | 3 * 4, a * b |
| /  |   나눗셈   | 3 / 4, a / b |
| %  |   나머지   | 3 % 4, a % b |

- 산술 연산자는 사칙연산을 다루는 기본적이면서도 가장 많이 사용되는 연산자이다
- 산술 연산자는 모두 두 개의 피연산자를 가지는 이항 연산자이며, 피연산자들의 결합 방향은 왼쪽에서 오른쪽이다
- 나머지 연산은 결과가 항상 정수이다

---

## 2. 관계 연산자 ( <, <=, >, >=, ==, != )

|             기호             |   기능    |          설명           |
|:--------------------------:|:-------:|:---------------------:|
|       <blockquote> >       |  a > b  |   a 가 b 보다 크면 true    |
|      <blockquote> >=       | a > = b | a 가 b 보다 크거나 같으면 true |
|       <blockquote> <       |  a < b  |   a 가 b 보다 작으면 true   |
|      <blockquote> <=       | a < = b | a 가 b 보다 작거나 같으면 true |
|      <blockquote> ==       | a == b  |   a 가 b 와 같으면 true    |
|      <blockquote> !=       | a != b  |  a 가 b 와 같지 않으면 true  |

- 비교 연산자의 결과 값은 크기 값을 비교하여 조건을 만족하면 true 그렇지 않으면 false를 반환한다
- 만약 비교되는 숫자의 데이터 타입이 다를 경우 기본적으로 크기가 큰 데이터 타입에 맞추어 비교 연산을 실행 한다

---

## 3. 비트 연산자

|       기호       |     기능     |                설명                |
|:--------------:|:----------:|:--------------------------------:|
| <blockquote>&& |   a && b   |       a, b 모두 true 이면 true       |
| <blockquote>II | a   II   b |    a, b 둘 중 하나라도 true 이면 true    |
| <blockquote>!  |     !a     | a 가 true 이면 false, false 이면 true |

**비트 연산자 ( &,|, ^)**
 - 비트 연산자는 두 수를 각각 2진수로 변환하여 두 수의 각 비트 연산을 수행한다
    - `& (비트곱)` : 두 비트가 1일때, 나머지는 0
    - `| (비트합)` : 두 비트 중 하나 이상이 1 이면 1, 두 비트 모두 0 이면 0
    - `^ (xor 배타적 논리합)` : 두 비트가 다르면 1, 같으면 0

**비트 이동 연산자 ( <<, >> )**
 - 왼쪽 항의 값을 2진수로 변환하여 오른쪽 항의 값만큼 비트를 왼쪽 (<<), 오른쪽 (>>), 으로 이동시키는 연산을 수행한다

---

## 4. 논리 연산자 (&, |, &&, ||)

- `&` : 연산을 수행하여 양쪽 항이 모두 true 일 때만 true 를 반환한다
- `|` : 연산을 수행하여 양쪽 항 중 한쪽만 true 를 만족해도 true 를 반환한다
- `&&` : 만일 왼쪽 항이 false 일 경우에는 오른쪽 항을 수행하지 않고 무조건 false 를 반환한다 ( 양쪽 항을 모두 검사하는 `&` 보다 속도가 빠름)
- `||` : 만일 왼쪽 항이 true 일 경우에는 오른쪽 항을 수행하지 않고 무조건 true 를 반환한다 ( 양쪽 항을 모두 검사하는 `|` 보다 속도가 빠름)

---

## 5. 대입 연산자 ( =, +=, -=, *=, /=, %= )

|       기호       |   기능    |       설명       |
|:--------------:|:-------:|:--------------:|
| <blockquote>=  | a = 9;  | 변수 a에 값 9 를 할당 |
| <blockquote>+= | a += b; |   a = a + b;   |
| <blockquote>-= | a -= b; |   a = a - b;   |
| <blockquote>*= | a *= b; |   a = a * b;   |
| <blockquote>/= | a /= b; |   a = a / b;   |
| <blockquote>%= | a %= b; |   a = a % b;   |

- 대입 연산자는 변수에 값을 대입할 때 사용하는 이항 연산자이며, 피연산자들의 결합 방향은 오른쪽에서 왼쪽이다
- 또한, 앞서 살펴본 산술 연산자와 결합한 다양한 복합 대입 연산자가 존재한다

---

## 6. 3항 연산자

| max = a > b ?  a : b; | a 가 b 보다 크면 a 의 값을 max 에 할당<br/>a 가 b 보다 크지 않다면 b 의 값을 max에 할당 |
|:---------------------:|:--------------------------------------------------------------:|

- 단순한 IF 문일 경우 라인수를 획기적으로 줄여주는 방식이 바로 3항 연산자이다
- 상함연산자는 (조건문) : ? 참 : 거짓 이라는 문법을 가지게 된다

```java
//IF ELSE
int a;
if(5<4) {
a = 50;
  }else {
a = 40;
  }
  System.out.println(a); //결과 = 40 

//삼항연산자
int b = (5 < 4) ? 50 : 40; 
System.out.println(b); //결과 = 40
```

- 위와 같이 삼항연산자가 할 수 있는 것은 IF ELSE 문을 통해서도 처리가 가능하다
- 삼항연산자를 사용하여 코드의 라인이 줄어들었다고 컴파일 속도가 빨라지는 것은 아니다
- 삼항연산자를 중복해서 처리할 경우, 가독성이 떨어질 수 있으므로 중복처리를 피하는 것이 좋다

---

> ## instanceof

 - 참조변수가 참조하고 있는 인스턴스의 실제 타입을 알아보기 위해 instanceof 연산자를 사용한다
 - 주로 조건문에 사용되며, instanceof 의 왼쪽에는 참조변수를 오른쪽에는 타입(클래스명)이 피연산자로 위치한다
 - 연산의 결과로 boolean 값인 true, false 중의 하나를 반환 한다
 - instanceof 를 이용한 연산결과로 true 를 얻었다는 것은 참조 변수가 검사한 타입으로 형 변환이 가능하다는 것을 뜻한다

> ## 화살표(->)연산자

람다식에 사용되는 연산자이다
 
 - 람다식이란 식별자없이 실행가능한 함수를 의미한다
 - 함수인데 함수를 따로 만들지 않고 코드한줄에 함수를 써서 그것을 호출하는 방식이다

```
(매개변수, ...) -> { 실행문 ... }
```

`매개변수, ...` 는 오른쪽 중괄호 `{}` 블록을 실행하기 위해 필요한 값을 제공하는 역할을 한다. 매개 변수의 이름은 개발자가 자유롭게 지정할 수 있으며 인자타입도 명시하지 않아도 된다. `->` 기호는 매개 변수를 이용해서 중괄호 `{}`바디를 실행한다는 뜻으로 해석하면 된다

**람다식 장점**

1. 람다를 사용하면서 만드는 무명함수는 재사용이 불가능하다
2. 코드가 간결하고 식에 개발자의 의도가 명확히 드러나므로 가독성이 향상된다
3. 함수를 만드는 과정없이 한번에 처리할 수 있기에 코딩하는 시간이 줄어든다
4. 병렬 프로그래밍이 용이하다

**람다식 단점**

1. 람다를 사용하면서 만드는 무명함수는 재사용이 불가능하다
2. 디버깅이 다소 까다롭다
3. 람다를 남발하면 코드가 지저분해질 수 있다 (비슷한 함수를 계속 중복생성할 가능성이 높다)
4. 재귀로 만들경우에는 다소 부적합한면이 있다

---

> ## 연산자 우선 순위

1. 최우선연산자 ( ., [], () )
2. 단항연산자 ( ++, --, !, ~, +/- : 부정, bit 변환 > 부호 > 증감 )
3. 산술연산자 ( *, /, %, +, -, shift ) < 시프트연산자 ( >>, <<, >>> ) >
4. 비교연산자 ( >, <, >=, <=, ==, != )
5. 비트연산자 ( &, |, ~)
6. 논리연산자 ( &&, ||, ! )
7. 삼항연산자 ( 조건식 ) ? :
8. 대입연산자 ( =, *=, /=, %=, +=, -= )

---

> ## (optional) Java 13. switch 연산자

Java 12 부터 프리뷰로 추가되었다

 `: 대신 -> 를 사용할 수 있다`
 
```java
int a = 1;

switch(a){
  case 1 -> System.out.println("case1");
  case 2 -> System.out.println("case2");
  }
```

`yield` 기능을 이용해 값을 리턴 할 수 있습니다

```java
int a = 1;
int b = switch (a) {
  case 1 -> {
    System.out.println("case1");
    yield 10;
  }
  case 2 -> {
    System.out.println("case2");
    yield 12;
  }
}
```
