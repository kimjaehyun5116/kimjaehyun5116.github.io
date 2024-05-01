---
title: "[Java] Java 데이터 타입, 변수 그리고 배열"

categories:
  - Java
tags:
  - [Java, Programming, coding]

toc: true
toc_sticky: true

date: 2024-05-01
last_modified_at: 2024-05-01
---

![java.png](/assets/images/java.png)

# **Java 데이터 타입, 변수 그리고 배열**

> 1. 프리미티브 타입 종류와 값의 범위 그리고 기본 값

![프리미티브](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ee861769-0783-455d-b68f-e3212f00440b/Untitled.png)

- 우리가 주로 사용하는 값의 종류는 크게 문자와 숫자로 나눌 수 있으며 여기서 숫자는 다시 정수와 실수로 나뉜다. 기본형은 모두 8가지의 타입(자료형)이 있으며, 크게 논리형, 문자형, 정수형, 실수형으로 구분된다

---

**<h3>타입 종류</h3>**

![타입종류](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ec3d40bb-f47b-496f-b941-99e18088a116/Untitled.png)

- 정수형은 가장 많이 사용되기에 타입이 4가지나 제공된다. 각 타입별로 범위가 다르기에 범위에 맞는 값을 사용하면 된다

---

**<h3>타입 범위</h3>**

![타입범위](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/41c48468-b97e-4614-a402-6ea73319a83f/Untitled.png)

- boolean은 true와 false 두 값만 표현하면 되기에 1바이트면 충분하다
  - 기본 값 : false
- char는 자바에서 유니코드(2 byte 문자 체계) 를 사용하기에 2byte
  - 기본 값 : 0
- int(4 byte)를 기준으로 짧게는 (2 byte) 길게는 (8 byte)취사 선택한다
  - 기본 값 : 0
- float은 실수값을 부동소수점(floating-point)방식으로 저장하기 때문에 float
  - 기본 값 : 0.0F
- double은 float보다 두 배의 크기(8 byte)를 갖기 때문에 double
  - 기본 값 : 0.

---

# 실수형의 정밀도

실수형은 정수형과 저장 방식이 다르기에 같은 크기라도 훨씬 큰 값을 표현할 수는 있지만, 오차가 발생할 수 있따. 그래서 정밀도(precision)가 중요한데, 정밀도가 높을수록 오차의 범위가 줄어든다

![실수형의정밀도](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/96a48e16-d423-4a5c-bf28-dce0d64f6a02/Untitled.png)

위 표를 보면 `float`의 정밀도는 7자리 10진수로 7자리의 수를 오차없이 저장할 수 있다는 의미이다<br/>
그렇기에 사용할 변수의 값의 범위가 7자리를 넘는다면 정밀도를 고려해 `double` 타입을 사용해야 한다

---

> 2. 프리미티브 타입과 레퍼런스 타입

자료형은 크게 '기본형(Primitive Type)'과 참조형(Reference Type)으로 나눌 수 있따

- 기본형(Primitive Type)
- 논리형(boolean), 문자형(char), 정수형(byte, short, int, long), 실수형(float, double) 계산을 위한 실제 값을 저장한다

- 참조형(Reference Type)
- 객체의 주소를 저장한다. 기본적으로 Java.lang.Object 를 상속받을 경우 참조형이 된다. 즉, 기본형을 제외하고는 참조형이라 생각해도 된다

좀 더 얘기하자면 기본형은 메로리영역의 스택영역에 실제 값들이 저장된다면, 참조형은 실제 인스턴스는 힙영역에 생성되있고, 그 영역의 주소를 스택영역에서 저장하고 있다고 보면 된다

---

> 3. 리터럴
