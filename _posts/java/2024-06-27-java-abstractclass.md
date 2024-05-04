---
title:  "[Java] 추상 클래스" 
categories: Java
tags: [Java, Programming, coding]
toc: true
toc_sticky: true
date:  2024-06-27
last_modified_at:  2024-06-27
---

![java.png](/assets/images/java.png)

# 추상 클래스

## 추상 클래스의 개념

자바는 일종의 미완성 클래스인 추상 클래스 `Abstract Class`를 지원한다. 일반 클래스는 `new` 연산자를 사용해 인스턴스를 생성할 수 있지만,
추상 클래스는 인스턴스를 생성할 수 없고 오직 상속을 통하여 완성된 자식 클래스로 구현해서 인스턴스를 생성할 수 있다. 추상 클래스는 단독으로 
사용할 수 없지만, 새로운 클래스를 작성하는 데 밑바탕은 될 수 있다

다음과 같이 도형, 원, 사각형, 원기둥을 모델링해 Shape, Circle, Rectangle, Cylinder 클래스로 작성한다고 하자  

![그림 7-1](/assets/images/ex7-1.png)

원기둥은 원의 특별한 형태이므로 원의 특성과 동작을 가진다. 원기둥을 모델링한 Cylinder 클래스는 원을 모델링한 Circle 클래스를 상속해 정의할 수 있다
원과 사각형은 도형의 일종이므로 도형의 특성과 동작을 가진다. 따라서 Circle 클래스와 Rectangle 클래스는 Shape 클래스를 상속해 정의 할 수 있다
원, 사각형, 원기둥과 달리 도형 자체는 구체적인 유형이 없어 그린다는 동작은 다소 추상적이다. 즉 Shape 클래스의 draw() 메서드를 어떻게 구현해야 
할지 알 수 없어 본체를 완전하게 작성할 수 없다.그러나 Shape 클래스는 메서드 이름과 매개변수 정보를 제시할 수 있다. 이런 완성하지 못한 메서드를 추상 메서드
`Abstract Method` 라고 한다. 추상 메서드는 무엇을 할지는 선언하지만, 어떻게 할지는 정의하지 않는다. 추상 메서드를 포함하는 클래스는 인스턴스
를 생성할 수 없으므로 추상 클래스이다. 추상 클래스는 보통 하나 이상의 추상 메서드를 포함하는데, 포함하지 않을 수도 있다.

추상클래스는 주로 상속 계층에서 자식멤버(필드, 메서드)의 이름을 통일하는 데 사용된다. 추상 클래스는 구현 클래스를 만드는 부모 클래스로만 사용할 뿐
new 연산자로는 인스턴스를 생성하지 못한다.

```java
추상클래스 s = new 추상클래스();✖ // 추상클래스는 인스턴스를 생성하지 못한다
```

---

## 추상 클래스의 선언

추상 클래스도 필드와 메서드를 포함할 수 있다. 심지어 생성자도 포함할 수 있는데 자식 객체가 부모 생성자 super()를 호출할 수 있기 때문이다.
추상 클래스는 다음과 같이 abstract 키워드로 선언하고 구현 클래스처럼 public 으로 지정할 수 있다.

```java
abstract class 클래스 이름 {     // abstract 는 추상 클래스라는 것을 나타낸다
  // 필드     
  // 생성자
  // 메서드            // 일반적으로 하나 이상의 추상 메서드를 포함한다
}
```

추상 메서드도 abstract 키워드를 붙여 선언하는데, 실체가 없기 때문에 본체 없이 세미콜론으로 끝난다. public 이나 protected 로 지정할 수 있다.

```java
abstract 반환타입 메서드 이름();     // 항상 세미콜론으로 끝나야 한다
// 메서드 본체가 없고 abstract 가 추상 메서드라는 것을 나타낸다
```

---

## 추상 클래스의 활용

원주율을 표시하는 필드, findArea() 메서드와 draw() 메서드로 구성된 Shape 클래스를 작성해보자. 도형은 넓이가 얿으므로 findArea()  메서드는
0.0을 반환하고, 그릴 수 없으므로 draw() 메서드는 본체 없는 추상 메서드로 선언할 수 있다.

```java
abstract  class Shape {
  double pi = 3.14;     // 추상 클래스도 멤버 필드를 포함할 수 있다
  
  abstract void draw();     // 추상 메서드는 본체가 없다
  
  public double findArea() {
    return 0.0;             // 추상 클래스도 구현 메서드를 포함할 수 있다
  }
}
```

Circle 클래스는 Shape 의 자식으로 작성할 수 있는데, 이때는 Shape 클래스의 추상 메서드인 draw() 메서드를 반드시 구현해야 한다.
Rectangle 클래스도 Circle 클래스와 비슷하게 작성할 수 있다.

```java
class Circle extends Shape {
  int radius;
  
  public Circle(int radius) {
    this.radius = radius;
  }
  
  public void draw() {
    System.out.println("원을 그리다.");      // 부모 클래스에서 추상 메서드로 선언했으므로 자식 클래스에서 반드시 구현해야 한다
  }
  
  public double findArea() {
    return pi * radius * radius;        // 부모 클래스의 메서드를 오버라이딩 한다
  }     // pi 는 부모 클래스인 Shape에서 물려받은 변수이다 
}
```

Shape 클래스의 생성자로 Shape 객체를 생성하면 오류가 발생한다. 따라서 Circle 클래스와 Rectangle 클래스를 사용해 객체를 생성해야 한다

```java
public class AbstractClassDemo {
  public static void main(String[] args) {
    // Shape s = new Shape();       // Shape 클래스는 추상 클래스이므로 생성자를 사용해 객체를 생성할 수 없다.
    
    Circle c = new Circle(3);
    c.draw();
    System.out.printf("원의 넓이는 %.1f\n", c.findArea());
    
    Rectangle r = new Rectangle(3, 4);
    r.draw();
    System.out.printf("사각형의 넓이는 %.1f\n", r.findArea());
  }
}
```

출력값

```
원을 그리다.
원의 넓이는 28.3
사각형을 그리다.
사각형의 넓이는 12.0
```