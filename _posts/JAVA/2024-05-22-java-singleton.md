---
title:  "[Java] singleton(싱글톤)" 

categories:
  -  Java
tags:
  - [Java, Programming, coding]

toc: true
toc_sticky: true

date:  2024-05-22
last_modified_at:  2024-05-22
---

![java.png](..%2Fassets%2Fimg%2Fjava.png)

## singleton-pattern 이란?
- 애플리케이션이 시작될 때 어떤 클래스가 최초 한 번만 메모리를 할당하고 그 메모리에 인스턴스를 만들어서 하나의 인스턴스를 공유해서 사용하며 메모리 낭비를 방지할 수 있게 함(매번 인스턴스 생성하지 않음)
### 장점
1. 첫 번재 이용 시에는 인스턴스를 생성해야하므로 속도차이가 나지 않으면 두 번째 이용 시에는 인스턴스 생성 시간 없이 사용할 수 있다
2. 인스턴스가 절대적으로 한 개만 존재하는 것을 보증할 수 있다

### 단점
1. 싱그론 인스턴스가 너무 많은 일을 하거나 많은 데이터를 공유하면 결합도가 높아진다(유지보수와 테스트 문제)
2. 동시성 문제를 고려해서 설계해야하기 때문에 난이도가 있다

### 싱글톤 구현 방법
1. 이른 초기화(Eager Initialization)
- 이른 초기화를 사용하면 클래스를 로드하는 속도가 느려지지만 처음 인스턴스 반환 요청에서 속도가 빠르다는 장점을 가진다
2. 게으른 초기화(Lazy Initialization)
- 게으른 초기화는 클래스 로드하는 속도는 빠르지만 첫 번째 요청에 대한 속도가 두 번째 요청에 대한 속도보다 느리다는 특징을 가지고 있다

<br>

- Application

```java
package com.ohgiraffers.section06.singleton;

public class Application {
    public static void main(String[] args) {
        
//        EagerSingleton eager = new EagerSingleton(); 생성자가 private라서 접근 불가
        EagerSingleton eager1 = EagerSingleton.getInstance();
        EagerSingleton eager2 = EagerSingleton.getInstance();

        System.out.println("eager1.hachcode = " + eager1.hashCode());
        System.out.println("eager2.hachcode = " + eager2.hashCode());

        LazySingleton lazy1 = LazySingleton.getInstance();
        LazySingleton lazy2 = LazySingleton.getInstance();

        System.out.println("lazy1.hashCode() = " + lazy1.hashCode());
        System.out.println("lazy2.hashCode() = " + lazy2.hashCode());

     }
}
```

- EagerSingleton

```java
package com.ohgiraffers.section06.singleton;

public class EagerSingleton {

    private static EagerSingleton eager = new EagerSingleton();

    private EagerSingleton(){}

    public static EagerSingleton getInstance(){return eager;}
}
```

-LazySingleton

```java
package com.ohgiraffers.section06.singleton;

public class LazySingleton {

    private static LazySingleton lazy;

    private LazySingleton(){}

    public static LazySingleton getInstance(){

        /*
        * 인스턴스를 생성한 적이 없는 경우 인스턴스를 생성해서 반환하고
        * 생성한 인스턴스가 있는 경우 만들어둔 인스턴스를 반환한다.
        * */
        if(lazy==null){
            lazy = new LazySingleton();

        }

        return lazy;
    }

}
```
### 요약. 싱글톤은 어떤 클래스가 단 하나의 인스턴스만을 가지고 있도록 보장하는 디자인 패턴이다. 이를 통해 해당 클래스의 인스턴스를 언제 어디서든지 쉽게 접근할 수 있다. 싱글톤은 보통 인스턴스 생성 및 관리에 대한 복잡성을 줄이고, 자원의 낭비를 방지하기 위해 사용된다


