---
title:  "[Java] absstractclass 추상클래스" 

categories:
  -  Java
tags:
  - [Java, Programming, coding]

toc: true
toc_sticky: true

date:  2024-06-19
last_modified_at:  2024-06-19
---

![java.png](/assets/images/java.png)

> # absstractclass 추상클래스

**추상 클래스와 추상 메서드**

- 추상 메소드를 0개 이상 포함하는 클래스를 추상 클래스라고 한다
- 추상 클래스는 클래스 선언부에 abstract 키워드를 명시해야한다
- 추상 클래스로는 인스턴스 생성이 불가능하다
- 추상 클래스는 사용하려면 추상 클래스를 상속 받는 하위 클래스를 이용하여 인스턴스를 생성해야 한다
- 이 때 추상클래스는 상위 타입으로 사용될 수 있으며 다형성을 이용할 수 있다
- 추상 클래스에 작성된 추상 메소드는 반드시 후손이 오버라이딩해서 작성해야 하며 후손 클래스들이 메소드들의 공통 인터페이스로의 역할을 수행할 수 있다
- 추상 클래스에 작성한 메소드를 호출하게 되면 실제 후손 타입의 인스턴스가 가지는 메소드는 다형성이 적용되어 동적 바인딩에 의해 다양한 응답을 할 수 있게 된다
- 추상 클래스를 상속받아 구현할 때는 extends 키워드를 사용하며 자바에서는 클래스를 상속받을 시 하나의 부모 클래스만 가질 수 있다

---

> # 추상 메소드란??

- 메소드의 선언부만 있고 구현부가 없는 메소드를 추상 메소드라고 한다
- 추상 메소드의 경우 abstract 키워드를 메소드 해드에 작성해야 한다
- 예) public abstract void method();

---

> # 추상 클래스를 쓰는 이유??

- 추상 클래스의 추상 메소드는 오버라이딩에 대한 강제성이 부여된다
- 따라서 여러 클래스들을 그룹화 하여 필수 기능을 정의하여 강제성을 부여해 개발 시 일관된 인터페이스를 제공할 수 있다
- 하지만 다른 클래스를 상속 받고 있는 클래스를 작성할 시에는 추상 클래스를 추가로 상속받을 수 없다
- 그래서 추상 클래스보다 더 강제성이 강한 인터페이스(interface)라는 매커니즘을 제공하고 있다

---

> 클래스를 만들어 연습

**Product**

```java
package section02.abstractclass;

public abstract class Product {
    private int nonStaticField;
    private static int staticField;
    public Product(){}

    public void nonStaticMethod(){

        System.out.println("Product 클래스의 nonStaticMethod 호출함...");
    }

    public static void staticMethod(){

        System.out.println("Product 클래스의 staticMethod 호출함...");
    }

    public void absMethod() {
    }
}
```

**abstractclass 코드리뷰**

1. 추상 클래스 선언

 - `public abstract class Product {`
 - 이부분은 `Product` 라는 추상 클래스를 선언한다
 - 추상 클래스는 `abstract` 키워드로 선언되며, 직접적으로 인스턴스화할 수 없다
 - 다른 클래스에서 확장하여 사용하는 것을 목적으로 한다

2. 필드

 - `private int nonStaticField;
   private static int staticField;`
 - 여기서 `nonStaticField`는 인스턴스 변수이고, `staticField`는 클래스(정적)변수이다
 - `nonStaticField`는 private 로 선언되어 `Product` 클래스 내에서만 접근할 수 있으며, `staticField`도 마찬가지로 private 잊만 모든 인스턴스에서 공유된다

3. 생성자

 - `public Product(){}`
 - 이 부분은 `Product`클래스의 기본 생성자이다
 - 어떠한 인자도 받지 않으며 특별한 초기화를 수행하지 않는다

4. 정적 메서드

 - `public static void staticMethod(){
   System.out.println("Product 클래스의 staticMethod 호출함...");
   }`
 - 이 부분은 `staticMethod`라는 정적 메서드이다
 - 클래스 자체와 관련이 있고 특정 인스턴스와는 관련이 없다
 - 호출되면 단순히 콘솔에 메세지를 출력한다

---

```java
package section02.abstractclass;

public class SmartPhone extends Product /*, java.util.Scanner*/ {

    public SmartPhone(){}

    @Override
    public void absMethod() {
        System.out.println("Product 클래스의 absMethod를 오버라이딩한 메서드 호출함...");
    }

    public void printSmartPhone(){
        System.out.println("SmartPhone 클래스의 메서드 printSmartPhone 호출함...");
    }

}
```

1. 클래스 선언

 - `public class SmartPhone extends Product /*, java.util.Scanner*/ {`
 - `SmartPhone`클래스는 `Product`클래스를 확장한다
 - Java는 단일 상속만 허용하기 때문에 다른 클래스를 확장할 수 없다

2. 추상 메서드 구현
 - `@Override
   public void absMethod() {
   System.out.println("Product 클래스의 absMethod를 오버라이딩한 메서드 호출함...");
   }`
 - `Product`클래스에서 상속받은 추상 메소드 `absMethod`를 구현한다
 - 이 메소드는 해당 클래스에서 특별한 작업을 수행하며, 부모 클래스의 메소드를 오버라이드한다

3. SmartPhone 특화 메소드

 - `public void printSmartPhone(){
  System.out.println("SmartPhone 클래스의 메서드 printSmartPhone 호출함...");
  }`
 - 이 메소드는 `SmartPhone`클래스에서만 존재하는 특별한 기능을 수행한다
 - 이 메소드는 다른 클래스에 상속되지 않는다

```java
package section02.abstractclass;

public class Application {
    private static Object SmartPhone;

    public static void main(String[] args) {

//      Produck produck = new Produck();  // 추상클래스는 인스턴스 생성불가

        SmartPhone SmartPhone = new SmartPhone();

        System.out.println(SmartPhone instanceof SmartPhone);
        System.out.println(SmartPhone instanceof Product);

        Product product = new SmartPhone();

        product.absMethod();

        product.nonStaticMethod();

        product.staticMethod();
        
    }
}
```

1. `SmartPhone` 인스턴스 생성

 - `SmartPhone SmartPhone = new SmartPhone();`

2. `instanceof`연산자 사용
 
 - `System.out.println(SmartPhone instanceof SmartPhone);
   System.out.println(SmartPhone instanceof Product);`
 - `instanceof`연산자를 사용하여 객체의 타입을 확인한다
 - 첫 번째 줄은 `SmartPhone`객체가 `SmartPhone`클래스의 인스턴스인지 확인하고, 두 번째 줄은 `SmartPhone`객체가 `Product`클래스의 인스턴스인지 확인한다

3. 다형성 사용
 
 - `Product product = new SmartPhone();`
 - 다형성을 이용하여 `Product`클래스의 참조 변수로 `SmartPhone`객체를 참조한다
 - 이렇게 하면 `Product`클래스의 메소드만 사용할 수 있지만, 실제로는 `SmartPhone`클래스의 오버라이딩된 메소드가 호출된다

4. 메소드 호출

 - `product.absMethod();
   product.nonStaticMethod();
   product.staticMethod();`
 - `Product` 클래스의 인스턴스로 호출된 메서드다
 - `absMethod`는 `SmartPhone` 클래스에서 구현된 메서드를 호출하며, `nonStaticMethod`는 `Product` 클래스에서 제공되는 메서드를 호출한다 
 - `staticMethod`는 정적 메서드이기 때문에 클래스 이름으로 호출된다.

**출력값**

```
true
true
Product 클래스의 absMethod를 오버라이딩한 메서드 호출함...
Product 클래스의 nonStaticMethod 호출함...
Product 클래스의 staticMethod 호출함...
```