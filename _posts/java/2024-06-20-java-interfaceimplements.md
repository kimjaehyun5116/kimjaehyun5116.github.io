---
title:  "[Java] interfaceimplements 인터페이스 구현" 
categories: Java
tags: [Java, Programming, coding]
toc: true
toc_sticky: true
date:  2024-06-20
last_modified_at:  2024-06-20
---

![java.png](/assets/images/java.png)

> # interfaceimplements 인터페이스 구현

**인터페이스**

- 인터페이스는 자바의 클래스와 유사한 형태지만 추상 메소드와 상수 필드만 가질 수 있는 클래스의 변형체를 말한다

**인터페이스의 사용목적**

1. 추상 클래스와 비슷하게 필요한 기능을 공통화해서 강제성을 부여할 목적으로 사용한다
2. 자바의 단일상속의 단점을 극복할 수 있다(다중 상속)

**interfaceimplements 클래스**

- 인터페이스가 인터페이스를 상속받을 시에는 extends 키워드를 사용하며 이때는 여러 인터페이스를 다중 상속 받을 수 있다
- 인터페이스는 상수 필드만 작성 가능하다
- public static final 제어자 조합을 상수 필드라고 부른다
- 반드시 선언과 동시에 초기화 해주어야한다.
- 인터페이스 안에 작성한 메서드는 묵시적으로 public abstract 의미를 가진다(다른 접근제한자 사용불가)
- 따라서 인터페이스 메소드를 오버라이딩 하는 경우 
- 반드시 접근제한자를 public 으로 해야 오버라이딩이 가능하다

```java
package section03.interfaceimplements;

public interface InterProduct extends java.io.Serializable/*, java.util.Comparator*/ {

    public static final int MAX_NUM = 100;

    /* 상수필드만 가질 수 있기 때문에 모든 필드는 묵시적으로 public static final이다 */
    int MIN_NUM = 10;

    /* 인터페이스는 생성자를 가질 수 없다. */
    // public interProduct(){}  //에러남

    /* 인터페이스는 구현부가 있는 non-static 메서드를 가질 수 없다.*/

//    public void nonStaticMethod(){};  //에러남

    /* 추상 메서드만 가능*/

    public abstract void nonStaticMethod();

    void absMethod();

    /*하지만, static 메서드는 작성이 가능하다. (JDK 1.8에 추가된 기능) */
    public static void staticMethod(){

        System.out.println("InterProduct 클래스의 staticMethod 호출됨...");


    }

    /* default 키워드를 사용하면 non-static 메서드도 작성 가능하다.(JDK 1.8에 추가된 기능) */
    public default void defaultMethod(){
        System.out.println("InterProduct 클래스의 defaultMethod 호출됨...");
    }
}
```

**interface InterProduct extends java.io.Serializable 코드리뷰**

1. 인터페이스 선언

 - `public interface InterProduct extends java.io.Serializable/*, java.util.Comparator*/ {`
 - `InterProduct`라는 이름의 인터페이스를 정의한다. 인터페이스는 `interface`키워드로 선언된다
 - 이 인터페이스는`java.io.Serializable` 인터페이스를 구현하고 있다

2. 상수 선언

 - `public static final int MAX_NUM = 100;
   int MIN_NUM = 10;`
 - `MAX_NUM`과 `MIN_NUM`이라는 두 개의 상수를 선언한다
 - 상수는 인터페이스 내에서는 자동으로 `public static final`로 선언되며, 명시적으로 선언하지 않아도 된다

3. 생성자 및 메소드 선언

 - `public interProduct(){}  //에러남
   public void nonStaticMethod();
   void absMethod();`
 - 생성자를 가질 수 없고, 구현부가 있는 메소드는 선언할 수 없으며, 추상 메소드만 가질 수 있다
 - 따라서 `interProduct()`와 `nonStaticMethod()`메소드는 주석 처리되어 있다
 - `absMethod`는 추상 메소드로서 구현되어야 한다

4. 정적(static)메소드 선언

 - `public static void staticMethod(){
   System.out.println("InterProduct 클래스의 staticMethod 호출됨...");
   }`
 - JDK 1.8 이상에서는 인터페이스에서 정적(static) 메소드를 선언할 수 있다
 - 이러한 메소드는 인터페이스 이름으로 직접 호출할 수 있다

5. 디폴트(default)메소드 선언
 
 - `public default void defaultMethod(){
   System.out.println("InterProduct 클래스의 defaultMethod 호출됨...");
   }`
 - JDK 1.8 이상에서는 인터페이스에서 디폴트(default)메소드를 선언할 수 있다
 - 이러한 메소드는 기본적으로 구현이 제공되고, 구현되지 않은 클래스에서는 이를 오버라이드 할 수 있다


** public class Product extends Object implements InterProduct, java.io.Serializable 클래스**

- 클래스에서 인터페이스를 상속 받을때는 implements 키워드를 사용한다 
- 또한 여러 인터페이스는 여러 개를 상속 받을 수 있으며, extends로 다른 클래스를 상속 받는 경우에도 그것과 별개로 인터페이스 수가 상속이 가능해진다
- 단, extends 키워드를 앞에 작성하고 implements 를 뒤에 작성한다 ( 순서 바뀌면 에러 발생)

```java
package section03.interfaceimplements;

public class Product extends Object implements InterProduct, java.io.Serializable {



    @Override
    public void nonStaticMethod() {
        System.out.println("InterProduct의 nonStaticMethod 오버라이딩한 메서드 호출됨...");
    }

    @Override
    public void absMethod() {
        System.out.println("InterProduct의 absMethod 오버라이딩한 메서드 호출됨...");


    }
    /* static 메소드는 오버라이딩 할 수 없다*/
    /*@Override
    public void staticMethod() {*/

    /*default 메서드는 인터페이스에서만 작성 가능하다.*/
    /*@Override
    public void defaultMethod() {*/



    public void defaultMethod() {
        System.out.println("product 클래식의 defaulMethod 호출됨");

    }

}
```

**코드 분석**

1. 클래스 선언

 - `Product`클래스를 정의한다
 - `implements`키워드를 사용하여 `InterProduct`인터페이스를 구현하고, `java.io.Serializable`인터페이스를 상속받는다
 - 또한, `Object`클래스를 명시적으로 상속받고 있다. Java에서는 클래스가 명시적으로 상위 클래스를 지정하지 않으면 `Object`클래스를 상속받게 된다

2. 메소드 오버라이딩

 - `InterProduct`인터페이스의 추상 메소드인 `nonStaticMethod()`와 `absMethod()`를 오버라이딩 한다
 - 클래스에서 인터페이스를 구현할 때는 인터페이스에 정의된 모든 추상 메소드를 제공해야 된다

3. 디폴트 메소드 재정의

 - `public void defaultMethod() {
   System.out.println("product 클래식의 defaulMethod 호출됨");
   }`
 - `InterProduct`인터페이스의 디폴트 메소드인 `defaultMethod()`를 재정의 한다
 - 클래스에서 디폴트 메소드를 재정의할 수 있다. 이렇게 함으로써 클래스에서는 자체적으로 구현을 제공할 수 있다

**public class Application**

```java
package section03.interfaceimplements;

public class Application {
    public static void main(String[] args) {
     
//        InterProduct interProduct = new InterProduct();     //에러남

        InterProduct interProduct = new Product();

        interProduct.nonStaticMethod();
        interProduct.absMethod();

        interProduct.defaultMethod();

        InterProduct.staticMethod();

        System.out.println(InterProduct.MAX_NUM);
        System.out.println(InterProduct.MIN_NUM);
    }
}
```

**코드분석**

1. `Product` 클래스의 인스턴스 생성

 - `InterProduct interProduct = new Product();`
 - `Product` 클래스의 인스턴스를 `InterProduct` 인터페이스 타입의 변수 `interProduct`에 할당한다
 - Java에서는 인터페이스를 구현한 클래스의 인스턴스를 해당 인터페이스 타입의 변수에 할당할 수 있다

2. 메소드 호출

 - `interProduct.nonStaticMethod();
   interProduct.absMethod();
   interProduct.defaultMethod();`
 - `interProduct` 변수를 통해 `InterProduct` 인터페이스의 메서드들을 호출한다
 - 이 때, 각 메소드들은 `Product`클래스에서 구현된 것들을 호출한다
 - `nonStaticMethod()`와 `absMethod()`는 추상 메서드이며, `defaultMethod()`는 디폴트 메서드다

3. 정적 메소드 호출

 - `InterProduct.staticMethod();`
 - `staticMethod()`는 정적 메서드이므로 클래스 이름으로 직접 호출할 수 있다. `staticMethod()`는 인터페이스인 `InterProduct`에서 제공된다

4. 인터페이스 상수 출력
 
  - `System.out.println(InterProduct.MAX_NUM);
    System.out.println(InterProduct.MIN_NUM);`
  - `InterProduct` 인터페이스의 상수인 `MAX_NUM`과 `MIN_NUM`에 접근하여 값을 출력한다

---

**출력값**

```
InterProduct의 nonStaticMethod 오버라이딩한 메서드 호출됨...
InterProduct의 absMethod 오버라이딩한 메서드 호출됨...
product 클래식의 defaulMethod 호출됨
InterProduct 클래스의 staticMethod 호출됨...
100
10
```