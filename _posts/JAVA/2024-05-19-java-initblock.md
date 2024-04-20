---
layout: post
title: "initblock(초기화 블럭)" 
date: 2024-05-19
excerpt: "초기화 블럭의 동작 순서를 이해하고 이를 활용하여 인스턴스를 생성할 수 있다"
tags: [java]
comments: true
---

![java.png](..%2Fassets%2Fimg%2Fjava.png)

## initblock(초기화 블럭)
- 복잡한 초기화를 수행할 수 있는 블럭을 제공하여, 인스턴스 초기화 블럭과 정적 초기화 블럭으로 구분된다
1. 인스턴스 초기화 블럭
- 인스턴스가 생성되는 시점에 생성자 호출 이전에 먼저 실행이 된다
- 인스턴스가 호출하는 시점마다 호출이 된다
- 인스턴스 변수를 초기화하며 정적필드에는 실행시마다 값을 덮어쓴다<br>
{<br>
초기화 내용 작성<br>
}<br>
2. 정적 초기화 블럭
- 클래스가 로드될 때 한 번 동작한다
- 정적 필드를 초기화하며, 인스턴스 변수는 초기화 하지 못한다<br>
static{<br>
초기화 내용 작성<br>
}<br>

- Application

```java
package com.ohgiraffers.section08.initblock;

public class Application {
    public static void main(String[] args) {
   
        Product product = new Product();

        /* 1. 자료형별 기본값으로 초기화 된 내용 확인 */
//        System.out.println("product.getInformation() = " + product.getInformation());

        /* 2. 명시적 초기화로 필드 초기화 확인 */

        System.out.println("product.getInformation() = " + product.getInformation());

        /* 3. 초기화 블럭으로 필드 초기화 확인 */
        System.out.println("초기화 블럭 product = " + product.getInformation());

        /* 4. 매개변수 있는 생성자를 이용한 초기화 확인 */
        Product product1 = new Product("대륙폰", 300000, "샤오미");
        System.out.println("product1.getInformation() = " + product1.getInformation());
        
    }
}
```

여기서 알 수 있는 초기화 순서는<br>
인스턴스 변수 : 기본값 -> 명시적 초기값 -> 인스턴스 초기화 블럭 -> 생성자<br>
클래스 변수 : 기본값 -> 명시적 초기값 -> 정적 초기화 블럭 -> 인스턴스 초기화 블럭 -> 생성자

- Product

```java
package com.ohgiraffers.section08.initblock;

public class Product {

    /* 1. 필드를 초기화 하지 않으면 JVM이 정한 기본값으로 객체가 생성된다. */

/*
    private String name;
    private int price;
    private  static  String brand;
*/

    /* 2. 명시적 초기화 */

    private String name = "갤럭시";
    private int price = 1000000;
    private static String brand = "삼송";

    /* 인스턴스 초기화 블럭 */
    {
        name = "사이언";
        price = 900000;

        brand = "사과";
        System.out.println("인스턴스 초기화 블럭 동작함...");

            }

    static {

//        name = "아이뿅";
//        price = 5500000;

        brand = "헬지";
        System.out.println("정적초기화 블럭 동작함...");

    }

    public Product(){
        System.out.println("기본생성자 호출됨...");
    }

    public Product(String name, int price, String brand) {
        this.name = name;
        this.price = price;
        Product.brand = brand;
        System.out.println("매개변수 있는 생성자 호출됨...");
    }

    public String getInformation() {

        return "Product [name=" + this.name + ", price=" + this.price + ", brand ="
                + Product.brand + "}";
    }
}
```

주의사항
- 인스턴스 초기화 블럭에서는 static 필드를 초기화 할 수 있는 것 처럼 보인다
- 하지만 static 초기화 블럭은 클래스 로드 될 때 이미 기본값으로 초기화를 진행했다
- 따라서 인스턴스 초기화 블럭이 동작하는 시점에는 이미 초기화가 진행된 정적 필드에 인스턴스 초기화 블럭에서 대입한 값으로 덮어쓰기 되는 것이다

static 주의사항
- static 초기화블럭에서는 non-static 필드를 초기화하지 못한다
- 정적 초기화 블럭은 클래스 로드시에 동작한다
- 따라서 정적 초기화 블럭의 동작 시점에는 인스턴스가 아무것도 존재할 수 없기 때문에 존재하지 않은 인스턴스 변수에 초기화 하는 것은 시기상으로 불가능하다


- 결과값

```
정적초기화 블럭 동작함...
인스턴스 초기화 블럭 동작함...
기본생성자 호출됨...
product.getInformation() = Product [name=사이언, price=900000, brand =사과}
초기화 블럭 product = Product [name=사이언, price=900000, brand =사과}
인스턴스 초기화 블럭 동작함...
매개변수 있는 생성자 호출됨...
product1.getInformation() = Product [name=대륙폰, price=300000, brand =샤오미}
```

### initblock"은 Java에서 클래스나 인스턴스가 생성될 때 실행되는 초기화 블록을 나타낸다

