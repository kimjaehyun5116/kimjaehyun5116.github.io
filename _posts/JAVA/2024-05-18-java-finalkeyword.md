---
title:  "[Java] final(최종변수)" 

categories:
  -  Java
tags:
  - [Java, Programming, Coding]

toc: true
toc_sticky: true

date:  2024-05-18
last_modified_at:  2024-05-18
---

![java.png](/assets/images/java.png)

## fianl
final 은 종단의 의미를 가지는 키워드이다<br>
final 키워드를 사용할 수 있는 위치가 다양한 편이며 의미가 약간은 다르지만, 결국 변경 불가의 의미이다
1. 지역변수 : 초기화 이후 값 변경 불가
2. 매개변수 : 호출시 전달한 인자 변경 불가
3. 전역변수 : 인스턴스 생성 후 초기화 이후에 값 변경 불가
4. 클래스(static) 변수 : 프로그램 start 이후 값 변경 불가
5. non-static 메소드 : 메소드 재작성 불가
6. static 메소드 : 메소드 재작성 불가
7. 클래스 : 상속 불가

## 1. non-static field 에 final 사용
- final 은 변경 불가의 의미를 가진다
- 따라서 초기 인스턴스가 생성되고 나면 기본값 0이 필드에 들어가게 되는데 그 초기화 이후 값을 변경할 수 없기 때문에 선언을 하면서 바로 초기화를 해주어야 한다
- 그렇지 않으면 compile error 가 발생한다

```java
package com.ohgiraffers.section06.finalkeyword;

public class FinalFieldTest {

    /* 선언과 동시에 초기화를 해주어야 한다.*/
//    private final int NON_STATIC_NUM; // 선언만 하면 에러남

    private final int NON_STATIC_NUM = 1;

    /* 생성자를 이용해서 초기화 함 */

    private final String NON_STATIC_NAME;

    public FinalFieldTest(String NON_STATIC_NAME) {
        this.NON_STATIC_NAME = NON_STATIC_NAME;
    }
    
//    private static final int STATIC_NUM;   // 에러남 // 0으로 초기화 되기 때문에 이후 값 변경 불가
    private static final int STATIC_NUM = 1;

    private static final double STATIC_DOUBLE;

    /*public FinalFieldTest(int STATIC_NAME) {
        this.STATIC_NAME = STATIC_NAME;*/

    /* 초기화 블럭으로는 가능하다. */
    static{
        STATIC_DOUBLE = 0.5;
    }
}
```

## 2. static field 에 final 사용
- static 에서도 자바에서 지정한 기본값이 대입되기 때문에 사용시 초기화를 하지 않으면 에러가 발생한다

### 생성자를 이용한 초기화 불가능
- 생성자는 인스턴스가 생성되는 시점에서 호출이 되기 때문에 그 전에는 초기화가 이루어지지 못한다
- 하지만 static 은 프로그램이 start 될 때 할당되기 때문에 초기화가 되지 않은 상태로 선언된 것과 동일하여 기본값으로 초기화된 후에 값을 변경하지 못하기 때문에 에러가 발생한다

- 출력값

```
eager1.hachcode = 295530567
eager2.hachcode = 295530567
lazy1.hashCode() = 1480010240
lazy2.hashCode() = 1480010240
```


### 요약. final 키워드는 변수, 메서드 또는 클래스에 사용되며, 변수의 경우 값이 한 번 할당되면 변경할 수 없고, 메서드의 경우 하위 클래스에서 재정의할 수 없으며, 클래스의 경우 상속할 수 없게 만든다

점점 어려워지는것 같다 정확히 말하면 어려운것과 머릿속 용량이 점점 커지면서 부담이 되는 듯 하다. 이럴때일 수록 복습복습!!..
