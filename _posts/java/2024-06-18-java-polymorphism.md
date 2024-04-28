---
title:  "[Java] polymorphism 다형성" 

categories:
  -  Java
tags:
  - [Java, Programming, coding]

toc: true
toc_sticky: true

date:  2024-06-18
last_modified_at:  2024-06-18
---

![java.png](/assets/images/java.png)

> # polymorphism (다형성)??

- 하나의 인스턴스가 여러가지 타입을 가질 수 있는 것을 의미한다
- 그렇기 때문에 하나의 타입으로 여러 타입의 인스턴스를 처리할 수 있기도 하고, 하의 메소드 호출로 객체별로 각기 다른 방법으로 동작할 수 있다
- 다형성은 객체지향 프로그래밍의 3대 특징 (캡슐화, 상속, 다형성) 중 하나이며, 객체지향 프로그램의 꽃이라고 불리울 정도로 활용성이 높고 장점이 많다. 하만 학습하기 어렵다는 단점을 가지고 있다

**다형성 장점**

1. 여러 타입의 객체를 하나의 타입으로 관리할 수 있기 때문에 유지보수성과 생산성이 장가한다
2. 상속을 기반으로 한 기술이기 때문에 상속관계에 있는 모든 객체는 동일한 메세지를 수신할 수 있다<br />
이런 동일한 메세지를 수신받아 처리하는 내용을 객체별로 다르게 할 수 있다는 장점을 가지고 있다<br />
(다양한 기능을 사용하는데 있어서 관리해야할 메세지 종류가 줄어들게 된다)<br />
하나의 호출로 여러가지 동작을 수행할 수 있다는 측면에서 오버라이딩을 다형성이라고 보기도 한다<br />
다형성을 이해하기 쉬운 가장 좋은 예 이기도 하다<br />
하지만 이 부분은 이견이 많이 존재하기 때문에 다형성을 이해하는데 참고로만 사용하자<br />
3. 확장성이 좋은 코드를 작성할 수 있다
4. 결합도를 낮춰서 유지 보수성을 증가시킬 수 있다

---

> ## Animal, Rabbit, Tiger 클래스를 만들어서 다형성을 사용해보자

```java
package section01.polymorphism

public class Applicatio1{
    public static void main(String[] args){
        
        /* Animal 인스턴스 생성 후 메소드 호출 확인 */
        Animal animal = new Animail();
        animal.eat();
        animal.run();
        animal.cry();

        System.out.println("=================================");

        /* Rabbit 인스턴스 생성 후 메소드 호출 확인 */
        Rabbit rabbit = new Rabbit();
        rabbit.eat();
        rabbit.run();
        rabbit.cry();
        rabbit.jump();

        System.out.println("=================================");

        /* Tiger 인스턴스 생성 후 메소드 호출 확인 */
        Tiger tiger = new Tiger();
        tiger.eat();
        tiger.run();
        tiger.cry();
        tiger.bite();

        System.out.println("=================================");

        /* 부모 타입으로 자식 인스턴스 주소값 저장 */
        Animal a1 = new Rabbit();
        Animal a2 = new Tiger();

        // Rabbit r = new Animail();           //에러남
        // Tiger r = new Animal();             //에러남

        /* 동적 바인딩 확인 */

        /* 동적 바인딩
            * 컴파일 당시에는 해당 타입의 메소드와 연결 되어있다가 
            * 런타입 당시의 실제 객체가 가진 오버라이딩된 메소드로 바인딩이 바뀌어 동작하는 것을 의미한다        
         */

        a1.cry();
        a2.cry();

        // a1.jump();      //에러남
        // a2.bite();      //에러남

        /* 타입형 변환 */
        System.out.println("================타입 형변환 확인================");
        ((Rabbit) a1).jump();
        ((Tiger) a2).bite();

        // ((Tiger) a1).bite();        // 토끼는 호랑이 될 수 없다

        /* instanceof 연산자 사용 확인 */
        System.out.println("================instanceof================");
        System.out.println("a1이 Tiger 타입인지 확인 : " + (a1 instanceof Tiger));
        System.out.println("a1이 Rabbit 타입인지 확인 : " + (a1 instanceof Rabbit));
        System.out.println("a1이 Animal 타입인지 확인 : " + (a1 instanceof Animal));
        System.out.println("a1이 Object 타입인지 확인 : " + (a1 instanceof Object));

        if (a1 instanceof Rabbit) {
            ((Rabbit) a1).jump();
        }
        if (a1 instanceof Rabbit){
            ((Tiger) a1).bite();
        }

        /* 클래스의 업캐스팅 다운 캐스팅 */

        /* 
            * 클래스 형변환은 up-casting 과 down-casting 으로 구분할 수 있다
            * up-casting : 상위 타입으로 형변환
            * down-casting : 하위 타입으로 형변환
            * 또한 작성 여부에 따라 명시적과 묵시적 두 가지로 구분한다
         */

        Animal animal1 = new Rabbit();                  // up-casting 묵시적 형변황
        Animal animal2 = (Animal) new Rabbit();         // up-casting 명시적 형변환

        Rabbit rabbit1 = (Rabbit) animal1;              // down-casting 명시적 형변환
        // Rabbit rabbit2 = animal2;                    // down-casting 묵시적 형변환이 안됨

    }
}
```

출력 값





**<h3>오버라이딩 성립요건</h3>**

1. 메소드 이름이 동일해야한다
2. 메소드의 리턴 타입이 동일해야한다
3. 매개변수 타입, 갯수, 순서가 동일해야 한다
4. private 메소드는 접근이 불가능하기 때문에 오버라이딩이 불가능하다
5. final 키워드가 사용된 메소드는 오버라이딩이 불가능하다
6. 접근제한자는 부모 메소드와 같거나 더 넓은 범위여야한다
7. 예외처리는 같은 예외거나 더 구체적(하위)인 예외를 처리해야한다

---

예제

```java
package section03.overriding;

public class SuperClass {

    public void method(int num){}

    private void privateMethod(){}

    public final void finalMethod(){}

    protected void protectedMethod(){}

}
```
```java
package section03.overriding;

public class SubClass extends SuperClass{

    /* 1. 메소드 이름을 변경하면 에러 발생*/
   /* @Override
    public void method2(int num) {
    }*/

    /*2. 메소드의 리턴타입 변경하면 에러발생*/
/*    @Override
    public int method(int num) {
        return 0;
    }*/

    /*3. 매개변수 갯수나 타입이 변경되면 에러발생*/
/*    @Override
    public void method(String num) {}*/

    /*4. 메소드이름, 리턴타입, 매개변수의 갯수, 타입, 순서가 일치할 경우 오버라이딩 성립.*/
    @Override
    public void method(int num) {}

    /*5. private 메소드는 오버라이딩 불가 */
/*    @Override
    private void privateMethod(){}*/

    /*6. final 메소드 오버라이딩 불가*/
 /*   @Override
    public final void finalMethod(){}*/

/*    @Override
    void protectedMethod(){}   //좁은 범위라서 불가능 */

  /*  @Override
    protected void protectedMethod() { //같은 범위
    }*/

    @Override
    public void protectedMethod() {} // 더 넓은 범위로도 가능

    /*참고로 클래스에도  final 키워드를 추가할 수 있는데 이는 상속을 제한하는 키워드이다.(클래스 확장 불가)*/
}
```

> ### 요약

`오버라이딩(Overriding)은 객체지향 프로그래밍에서 기존에 정의된 메서드를 서브클래스에서 새로운 내용으로 다시 정의하는 것을 말한다. 
이는 상속 관계에서 부모 클래스의 메서드를 자식 클래스에서 재정의하여 사용하는 개념이다. 
오버라이딩을 통해 자식 클래스는 부모 클래스의 동작을 수정하거나 확장할 수 있다. 
이는 다형성의 중요한 개념 중 하나이며, 코드의 재사용성과 유연성을 높여준다.`
