---
title:  "[Java] static keyword" 

categories:
  -  Java
tags:
  - [Java, Programming, Coding]

toc: true
toc_sticky: true

date:  2024-05-17
last_modified_at:  2024-05-17
---

![java.png](/assets/images/java.png)

## static
- 정적 메모리 영역에 프로그램이 start 될 때 할당하는 키워드이다
- 인스턴스를 생성하지 않고도 사용할 클래스의 맴버(필드, 메소드)를 지정할 수 있다
- 여러 인스턴스가 공유해서 사용할 목적의 공간이다
- 하지만 static 키워드의 남발은 유지보수와 추적이 힘든 코드를 작성하는 피해야할 방식이다
- 명확한 목적이 존재하지 않는 이상 static 키워드 사용은 자제하도록 한다
- 의도적으로 static 키워드를 사용하는 대표적인 예는 singleton 객체를 생성할 때이다

<br>

- Application

```java
package com.ohgiraffers.section06.statickeyword;

public class Application {
    public static void main(String[] args) {
        /* static 키워드는 필드에서 사용 */
        StaticFieldTest sft = new StaticFieldTest();

        System.out.println("non.static filed = " + sft.getNonStaticCount());    //0
        System.out.println("static filed = " + sft.getStaticCount());    //0

        sft.increaseNonStaticCount();
        sft.increaseStaticCount();

        System.out.println("non.static filed = " + sft.getNonStaticCount());    //1
        System.out.println("static filed = " + sft.getStaticCount());    //1


        StaticFieldTest sft2 = new StaticFieldTest();

        System.out.println("non.static filed = " + sft2.getNonStaticCount());    //0
        System.out.println("static filed = " + sft2.getStaticCount());   //1
        
        StaticMethodTest smt = new StaticMethodTest();

        smt.nonStaticMethod();

//        smt.staticMethod();     // 권장하지 않음

        StaticMethodTest.staticMethod(); //권장함

    }
}
```
- 인스턴스 변수의 경우에는 sft 과 sft2 두 개의 인스턴스가 서로의 값을 공유하지 못하고 인스턴스를 생성할 때마다 0으로 초기화 되었다
- static 필드의 경우에는 클래스 변수 자체가 프로그램이 종료할 때까지 유지되고 있기 때문에 값을 유지하고 있다
- 따라서 여러 개의 인스턴스가 같은 값(공간)을 공유할 목적으로 static 키워드를 사용한다

<br>

- StaticFieldTest

```java
package com.ohgiraffers.section06.statickeyword;

public class StaticFieldTest {

    private int nonStaticCount;
    private static  int staticCount;

    public StaticFieldTest(){}

    public int getNonStaticCount() {
        return this.nonStaticCount;
    }

    public int getStaticCount() {
        return StaticFieldTest.staticCount;
    }


    public void increaseNonStaticCount(){this.nonStaticCount++;}

    public void increaseStaticCount(){StaticFieldTest.staticCount++;}
}
```

- StaticMethodTest

```java
package com.ohgiraffers.section06.statickeyword;

public class StaticMethodTest {

    private int count;

    public void nonStaticMethod(){

        this.count++;
        System.out.println("nonStaticMethod 호출함...");
    }

    public static void staticMethod(){

//        this.count++;

        System.out.println("StaticMethod 호출함...");
    }


}
```

- 출력값

```
non.static filed = 0
static filed = 0
non.static filed = 1
static filed = 1
non.static filed = 0
static filed = 1
nonStaticMethod 호출함...
StaticMethod 호출함...
```

### 요약. static 키워드는 클래스의 인스턴스에 속하지 않고 클래스 자체에 속하는 멤버를 정의할 때 사용되며, 인스턴스를 생성하지 않고도 접근할 수 있다


