---
title:  "[Java] kinds of Variable" 

categories:
  -  Java
tags:
  - [Java, Programming, coding]

toc: true
toc_sticky: true

date:  2024-05-20
last_modified_at:  2024-05-20
---


![java.png](/assets/images/java.png)

## kinds of Variable
- 클래스 영역에 작성하는 변수를 필드라고 한다
- 필드 == 맴버변수(클래스가 가지는 맴버라는 의미) == 전역변수(클래스 전역에 사용할 수 있는 변수라는 의미)
- non-static field 를 인스턴스변수 라고 한다(인스턴스 생성 시점에서 사용가능한 변수라는 의미)

- Application

```java
package com.ohgiraffers.section07.kindsofVariable;

public class Application {
    public static void main(String[] args) {

        KindsofVariable kd = new KindsofVariable();
        kd.testMethod(200);

        kd.testMethod2();
    }
}
```

- kinds of Variable

```java
package com.ohgiraffers.section07.kindsofVariable;

public class KindsofVariable { //클래스 영역의 시작
    
    private int globalNum;

    /* static field를 정적필드(클래스변수)라고 한다. 정적(클레스)영역에 생성되는 변수라는 의미이다.  */

    private static int staticNum;
    public void testMethod(int num) {   //메소드 영역의 시작
    
        int localNum;
        System.out.println("num = " + num);     //매개변수는 호출시 값이 넘어와서 변경되기 때문에 초기화가 필요없다.


        /* 지역변수는 선언 외에 사용(호출하기 위해서는 반드시 초기화가 되어야 한다)*/
       // System.out.println("localNum = " + localNum);
        System.out.println("globalNum = " + globalNum); //전역변수는 클래스 전역에서 사용 가능
        System.out.println("staticNum = " + staticNum);


    }

    public void testMethod2(){
//        System.out.println("num = " + num); //지역변수는 해당 지역(블럭 내)에서만 사용 가능하다.
        System.out.println("globalNum = " + globalNum);
        System.out.println("staticNum = " + staticNum); // 지역변수는 다른 매소드에서도 사용할 수 있다.
    }

}
```

- 메소드 영역에서 작성하는 변수를 지역변수라고 한다
- 메소드 괄호 안에 선언하는 변수를 매개변수라고 한다
- 매개변수도 일종에 지역변수로 생각하면 된다
- 지역변수도 매개변수도 모두 메소드 호출 시 stack 을 할당받아  stack 에 생선된다
- 출력값

```
num = 200
globalNum = 0
staticNum = 0
globalNum = 0
staticNum = 0
```



