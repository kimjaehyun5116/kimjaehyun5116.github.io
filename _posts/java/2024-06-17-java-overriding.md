---
title:  "[Java] overriding 오버라이딩" 

categories:
  -  Java
tags:
  - [Java, Programming, coding]

toc: true
toc_sticky: true

date:  2024-06-17
last_modified_at:  2024-06-17
---

![java.png](/assets/images/java.png)

> # overriding (오버라이딩)??

- 부모 클래스에서 상속 받은 메소드를 자식 클래스에서 재정의 하여 사용하는 것이다

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
