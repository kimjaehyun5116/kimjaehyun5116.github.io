---
title:  "[Java] 인터페이스 기본" 
categories: Java
tags: [Java, Programming, coding]
toc: true
toc_sticky: true
date:  2024-05-04
last_modified_at:  2024-05-04
---

![java.png](/assets/images/java.png)

# 인터페이스 기본

## 개요

제품을 나누어 개발한 후 하나로 합칠 때 미리 규격을 정하지 않으면 나중에 문제가 발생할 수 있다. 이때 필요한 것이 인터페이스 `interface`로 사전에 
정한 약속이나 규격을 의미한다. 인터페이스 덕분에 전자제품의 종류에 관계없이 동일한 전기 콘센트를 사용할 수 있는 것이다

![그림 7-2](/assets/images/ex7-2.png)

다수의 개발자가 소프트웨어를 개발하려면 각 클래스를 통합할 약속이 필요한데, 자바는 이 약속을 인터페이스로 정의한다. 인터페이스는 클래스 간에
상호작용하는 규격으로, 사용 방법이 같은 클래스를 만드는 기술이다. 예를들어 그림과 같이 왼쪽 객체는 오른쪽에 있는 네가지 객체의 모양이나 색상에 
관계없이 빨간색 실선 부분만 서로 맞으면 통합할 수 있다. 여기서 빨간 실선 부분이 인터페이스에 해당한다

![그림 7-3](/assets/images/ex7-3.png)

인터페이스를 이용하면 다음 장점을 얻을 수 있다

- 인터페이스만 준수하면 통합에 신경 쓰지 않고 다양한 형태로 새로운 클래스를 개발할 수 있다
- 클래스의 다중 상속을 지원하지 않지만, 인터페이스로 다중 상속 효과를 간접적으로 얻을 수 있다

인터페이스와 추상 클래스는 추상화라는 동일한 목적을 가지지만, 다른 점도 많다. 일부 메서드를 추상화한 추상 클래스와 달리 인터페이스는 모든 맴버를
추상화하므로 추상 클래스의 단적인 예라고 할 수 있다. 인터페이스와 추상 클래스를 사용할 때는 다음 특징을 고려해야 한다

**인터페이스와 추상 클래스의 차이**

|분류|인터페이스| 추상 클래스        |
|-|-|---------------|
|구현 메서드|포함 불가(단, 디폴트 메서드와 정적 메서드는 예외)| 포함가능          |
|인스턴스 변수|포함 불가능| 포함 가능         |
|다중 상속|가능| 불가능           |
|디폴트 메서드|선언 가능| 선언 불가능        |
|생성자와 main()|선언 불가능| 선언 가능         |
|상속에서의 부모|인터페이스| 인터페이스, 추상 클래스 |
|접근 범위|모든 멤버를 공개|추상 메서드를 최소한 자식에게 공개|

추상 클래스에서 추상 메서드는 반드시 자식 클래스에 상속해야 하므로 public 이나 protected 로 지정되어야 하지만, 나머지 멤버는 어떤 접근 지정자로도 지정할 수 있다

---

## 디폴트 메서드와 정적 메서드

`JDK 8` 에서는 하위 호환성을 유지하면서 기존 인터페이스에 새로운 기능을 추가할 수 있도록 디폴트 메서드 `Default Method` 를 지원한다.
디폴트 메서드를 이용하면 기존에 사용하던 인터페이스의 구현 클래스에 영향을 주지 않고도 인터페이스를 변경할 수 있다.

예를 들어 어떤 인터페이스를 구현한 클래스가 이미 사용되고 있는 상태에서 그 인터페이스를 수정해야 한다고 가정해보자. 그람과 같이
`method1()` 메서드로 구성된 인터페이스 `A`에 새로운 추상 메서드인 `method2()`를 추가하면 기존에 구현한 클래스는 `method2()` 메서드를 구현하지 
않아 모두 오류가 발생한다. 이런 문제점을 디폴트 메서드가 해결한다.

![그림 7-4](/assets/images/ex7-4.png)

디폴트 메서드는 인터페이스의 멤버이지만 구현 메서드로 다음과 같이 반환 타입 앞에 `default` 라고 명시해야 한다.

```java
default 반환타입 디폴트메서드이름( ) {
  // 본체를 구성하는 코드
}
```

인터페이스 A에 디폴트 메서드를 추가하더라도 기존 구현 클래스는 디폴트 메서드를 구현하지 않아도 되므로 오류 없이 그대로 사용할 수 있다.

![그림 7-5](/assets/images/ex7-5.png)

```
⭐ 인터페이스나 추상 클래스를 구현한 클래스를 문맥상 추론할 수 있으면 그냥 구현 클래스라고 한다. 인터
페이스나 추상 클래스 이름이 A라면 그 구현 클래스를 A 구현 클래스라고 한다. 그리고 구현 클래스로 생
성한 객체를 그냥 구현 객체라고 한다.
```

반면 정적 메서드는 구현된 본체를 가진다는 점에서 디폴트 메서드와 비슷해 보이지만, 근복적으로는 다르다. 디폴트 메서드는 오버라이딩될 수 있지만,
정적 메서드는 오버라이딩될 수 없다. 디폴트 메서드는 인스턴스 메서드이므로 객체를 생성한 후 호출하지만, 정적 메서드는 인터페이스로 직접 호출한다.

---

## 인터페이스의 구조

인터페이스는 무엇을 할지 명시하지만, 어떻게 구현할지는 명시하지 않는다.인터페이스는 클래스와 문법이 유사하지만 인스턴스 변수를 선언할 수 없고, 
객체도 생성할 수 없기 때문에 생성자가 없다. 또 디폴트 메서드와 정적 메서드가 아닌 메서드는 본체 없는 추상 메서드로만 선언할 수 있다.

인터페이스는 `interface` 키워드로 정의하며 구조는 다음과 같다. 모든 멤버가 선택 사항으로 하나 이상을 포함할 수 있다

```java
interface 인터페이스이름 {
  // 상수 필드              상수만 가능하기 때문에 public static final 키워드가 없어도 된다.
  
  
  // 추상 메서드            interface 의 모든 메서드가 public abstract 이기 때문에 public abstract 를 생략해도 된다   
        
  // 디폴트 메서드           JDK 8 부터 선언할 수 있다
  
  //정적 메서드
}
```

인터페이스 멤버에 명시된 `public`, `static`, `final`, `abstract` 키워드는 생략할 수 있다. 생략한 키워드는 컴파일할 때 자동으로 추가한다. 
인터페이스 파일 확장자는 `java`로, 컴파일하면 확장자가 `class`인 파일을 생성한다.

![그림 7-6](/assets/images/ex7-6.png)

인터페이스는 완전히 추상화된 것으로 인스턴스를 생성할 수 없다. 인터페이스를 사용하려면 궁금적으로 인터페이스를 구현한 클래스를 작성해야 한다.

---

## 인터페이스의 상속

인터페이스도 `extends` 키워드를 사용해 자식 인터페이스를 정의할 수 있다. 그리고 인터페이스로 자식 클래스를 정의하려면 추상 메서드를 구현해야 하므로, 
`implements`키워드를 사용한다

```java
// 인터페이스를 상속하려면 extends 키워드를 사용한다.
interface 자식인터페이스 extends 부모인터페이스 {
}

// 인터페이스를 구현하려면 implements 키워드를 사용한다.
class 자식클래스 implements 부모인터페이스 {
}
```

인터페이스가 클래스의 자식이 될 수 없는 것을 제외한 모든 상속 관계가 클래스와 인터페이스 사이에 가능하다.

![그림 7-7](/assets/images/ex7-7.png)

다수의 인터페이스를 상속해 새로운 자식 인터페이스나 구현 클래스를 작성할 수 있다.

```java
// 상속할 인터페이스가 여러 개라면 쉼표(,)로 연결한다.
interface 자식인터페이스 extends 부모인터페이스1, 부모인터페이스2 {
}
class 자식클래스 implements 부모인터페이스1, 부모인터페이스2 {
}
```

심지어 다수의 인터페이스와 하나의 클래스를 상속해 구현 클래스를 작성할 수도 있다. 반면 자바는 둘 이상의 클래스를 상속한 자식 클래스를 작성할 수는 없다

```java
// 인터페이스는 다중 상속할 수 있다.
class 자식클래스 extends 부모클래스 implements 부모인터페이스1, 부모인터페이스2 {
}

// 클래스는 다중 상속할 수 없다.
class 자식클래스 extends 부모클래스1, 부모클래스2 {
}
```

다음과 같이 다수의 인터페이스를 상속해 자식 인터페이스도 작성할 수 있고, 인터페이스와 클래스를 상속해 자식 클래스도 작성할 수 있다.

![그림 7-8](/assets/images/ex7-8.png)

---

# 인터페이스 응용

## 인터페이스와 상수

상수를 인터페이스에 정의하면 여러 종류의 클래스에서 사용할 수 있어 편리하다. 예를들어 동전과 관련된 상수를 인터페이스에 정의한 후 사용해보자

- 상수를 정의한 인터페이스

```java
interface Coin {
  int PENNY = 1, NICKEL = 5, DIME = 10, QUARTER = 25;
  // int 만 표시되어 있지만, public static final int 이다. 인터페이스의 모든 필드는 public static final 이기 떄문이다
}

public class Coin1Demo {
  public static void main(String[] args) {
    System.out.println("Dime 은" + Coin.DIME + "센트입니다.);
                                 //  인터페이스에 정의된 상수 DIME 를 의미한다.
  }
}
```

- 출력값

```
Dime은 10센트 입니다.
```

다음은 테스트 프로그램은 `Coin` 인터페이스의 구현 클래스로 사용하는 예제이다

- 구현 클래스로 테스트

```java
public class Coin2Demo implements Coin {
                    // Coin 인터페이스를 구현한다. Coin 인터페이스가 추상 메서드를 포함하지 않으므로 추가할 코드가 없다.
  public static void main(String[] args) {

    System.out.println("Dime은" + DIME + "센트입니다.");
                                // Coin 인터페이스의 구현 클래스이므로 직접 상수를 사용할 수 있다.
  }
}
```

## `Comparable` 인터페이스

자바가 제공하는 기본 인터페이스는 다양하다. 그중 객체를 비교하기 위한 규격으로 사용되는 `Comparable` 인터페이스는 다음과 같이 정의되었다

```java
public interface Comparable {
  int compareTo(Object other);      // 다른 객체보다 크면 양수, 동일하면 0, 작으면 음수를 반환한다.
}
```

`Comparable` 구현 클래스는 객체를 비교할 수 있다. `Circle` 클래스가 `Comparable` 구현 클래스일 때 `Circle` 객체를 서로 비교할 수 있는 예제

- `Comparable` 인터페이스의 응용

```java
class Circle implements Comparable {
  double radius;
  
  public Circle(double radius) {
    this.radius = radius;
  }
  
  public int compareTo(Object o) {
    Circle c = (Circle) 0;      // Object 객체를 Circle 클래스로 타입 변환해서 사용한다.
    if (this.radius > c.radius)
      return 1;
    else if (this.radius == c.radius)       // Comparable 인터페이스에 포함된 추상 메서드로 구현 클래스에서 반드시 구현해야 한다.
      return 0;
    else return -1;
  }
}

public class CircleDemo {
  public static void main(String[] args) {
    Circle c1 = new Circle(5.0);
    Circle c2 = new Circle(6.0);
    
    if (c1.compareTo(c2) > 0)
      System.out.println("첫 번째 원이 두번째 원보다 크다.");
    else if (c1.compareTo(c2) == 0)
      System.out.println("두 원의 크기가 같다.");
    else
      System.out.println("첫 번째 원이 두번째 원보다 작다.");
  }
}
```

- 출력값

```
첫 번째 원이 두번째 원보다 작다.
```

---

## 인터페이스의 상속과 구현 클래스

전자제품에 포함되어야 하는 제어부가 요구하는 조건이다. 이 제어부를 인터페이스로 작성해보자

1. 모든 전자제품에는 전원을 온•오프하는 기능이 있으며, 수리 및 공장 초기화를 할 수 있다.
2. 전자제품 객체는 `turnOn()` 메서드, `turnOff()` 메서드로만 전원을 조절할 수 있어야 한다.
3. 수리 및 공장 초기화 기능을 미리 구현해 놓아서 필요할 때 사용할 수 있어야 한다.
4. 수리 기능은 자식 클래스에서 오버라이딩할 수도 있다.

요구 조건에 따라 수리 및 공장 초기화 기능을 구현해야 하므로 디폴트 메서드나 정적 메서드로 작성한다. 그런데 수리 기능은 자식 클래스가 오버라이딩
할 수 있으므로 디폴트 메서드로 작성하면 된다.

- 전자제품 제어부 인터페이스

```java
public interface Controllable {
  default void repair() {
    System.out.println("장비를 수리한다.");        // 디폴트 메서드이다.
  }
  
  static void reset() {
    System.out.println("장비를 초기화한다.");       // 정적 메서드이다.
  }
  
  void turnOn();        // 추상 메서드이다.
  void turnOff();
}
```

위의 예제의 인터페이스를 상속해 `RemoteControllable` 이라는 새로운 인터페이스를 작성하는 예제이다

- `Controllable` 자식 인터페이스

```java
public interface RemoteControllable extends Controllable {
                                  // 인터페이스도 상속받을 때는 extends 키워드를 사용한다
  void remoteOn();
                // RemoteControllable 인터페이스에 새로 추가한 메서드이다.
  void remoteOff();
}
```

`RemoteControllable` 인터페이스는 `remoteOn()` 메서드, `remoteOff()` 메서드 외에 부모 인터페이스인 `Controllable`의 `turnOn()`메서드,
`turnOff()` 메서드도 사용할 수 있다.

TV 클래스를 다음과 같이 `Controllable`구현 클래스로 작성하면 TV 클래스에서 `Controllable`인터페이스의 `turnOn()` 메서드, `turnOff()` 메서드를 사용할 수 있다.

- `Controllable` 구현 클래스인 Tv

```java
public class TV implements Controllable {
  
  @Override
  public void turnOn() {            // Controllable 인터페이스에 정의된 모든 추상 메서드를 구현해야 한다.
    System.out.println("TV를 켠다.");
  }
  
  @Override
  public void turnOff() {           // 반드시 public 이어야 한다. 자식은 부모보다 접근 범위가 좁으면 안 되기 때문이다. 부모인 인터페이스의 메서드는 모두 public 이다.
    System.out.println("TV를 끈다.");
  }
}
```

모든 전자제품 클래스를 `Controllable` 구현 클래스로 작성하면 개발자가 전자펨 관련된 객체를 일관된 방법으로 사용할 수 있기때문에 코드가 단순해진다.
예를들어 전원을 연결하면 전자제품의 종류와 관계없이 `turnOn()` 메서드를 호출하면된다. 그런데 인터페이스 없이 작성한다면 작성하는 개발자마다 `turnOn()`, `PowerOn()`,
`On()` 등 각자 다르게 사용할 수 있어 코드가 복잡해질 수 있다.

`TV`와 `Computer` 둘다 `Controllable` 구현 클래스일때 효과를 확인해보자

- `Controllable` 인터페이스의 테스트

```java
public class ControllableDemo {
  public static void main(String[] args) {
    TV tv = new TV();
    Computer com = new Computer();
    
    tv.turnOn();
    tv.turnOff();
    tv.repair();            // Controllable 인터페이스로 TV 객체와
    com.turnOn();           // Computer 객체를 동작하는 방법이 같다.
    com.turnOff();
    com.repair();
    Controllable.reset();       // 정적 메서드는 인터페이스로 직접 호출해야 한다.
    // tv. reset();     
    // com.reset();
  }
}
```

- 출력값

```
TV를 켠다.
TV를 끈다.
장비를 수리한다.
컴퓨터를 켠다.
컴퓨터를 끈다.
장비를 수리한다.
장비를 초기화한다.
```

`Computer` 클래스와 `Portable` 인터페이스를 부모로 사용해 `Notebook` 클래스를 구현하는 예제

- 클래스와 인터페이스의 자식 클래스

```java
interface Portable {
  void inMyBAG();
}

public class Notebook extends Computer implements Portable {
  public void inMyBag() {
    System.out.println("노트북은 가방에 있다.");     // Portable 인터페이스의 메서드를 구현한다.
  }
  
  public void turnOn() {
    System.out.println("노트북을 켠다.");
  } 
                                        // Computer 클래스의 메서드를 오버라이딩한다.
  public void turnOff() {
    System.out.println("노트북을 끈다.");
  }

  public static void main(String[] args) {
    Notebook n = new Notebook();        // 자신의 생성자를 호출해도 괜찮다. 
                                        // 단, 생성자 내부에서 호출할 때는 this()를 사용해야 한다.
    n.turnOn();
    n.turnOff();
    n.inMyBag();
  }
}
```

- 출력값

```
노트북을 켠다.
노트북을 끈다.
노트북은 가방에 있다.
```

---

# 인터페이스와 다형성

## 인터페이스 타입

인터페이스도 클래스처럼 하나의 타입이므로 변수를 인터페이스 타입으로 선언할 수 있다. 인터페이스의 구현 클래스는 그 인터페이스의 자식 타입이다.
따라서 구현 클래스의 객체인 구현 객체는 인터페이스 타입이므로 인터페이스 타입 변수에 대입할 수 있다. 구현 객체를 다음과 같이 인터페이스 타입 
변수에 대입하면 자동으로 인터페이스 타입으로 변환된다.

```java
인터페이스타입 변수 = 구현객체     //구현 객체는 인터페이스 타입이므로 자동 변환된다.
```

상속에서 사용한 다형성을 인터페이스에서도 응용할 수 있다. 즉, 인터페이스 타입에 다양한 인터페이스 구현 객체를 대입하면 구현 객체의 종류에 따라 다르게 실행할 수 있다.

인터페이스 타입 변수로는 인터페이스 멤버만 볼 수 있고 구현 클래스에 추가된 멤버는 볼 수 없다. 구현 클래스에 추가된 멤버에 접근하려면 강제로 타입을 변환해야 된다.
단, 인터페이스 타입 변수가 구현 객체를 참조할 때만 강제로 타입을 변환할 수 있다.

![exex1](/assets/images/exex1.png)

---

## 타입 변환과 다형성

비슷한 코드가 반복되면 지저분하고 가독성이 떨어진다. 다형성을 이용하면 코드가 단순하고 가독성 있게 작성할 수 있다.

- 인터페이스와 다형성 1


```java
import sec03.Computer;
import sec03.Controllable;
import sec03.TV;

public class ControllableDemo {
  public static void main(String[] args) {
    controllable[] controllable = { new TV(), new Computer() }; 
    // 인터페이스 타입의 배열 변수에 구현 객체 배열을 대입한다.
    
    for (Controllable c : controllable) {
      c.turnOn();
      c.turnOff();          // 인터페이스 타입 변수를 사용해 구현 객체의 메서드를 호출한다
      c.repait();
    }
    Controllable.reset();
  }
}
```

구현 객체를 인터페이스 타입의 인수로 대입해보자

- 인터페이스와 다형성 2

```java
interface Animal {
  void sound();
}

class Dog implements Animal {
  public void sound() {
    System.out.println("멍멍~");
  }
}                                // Animal 구현 클래스이다.

class Cuckoo implements Animal {
  public void sound() {
    System.out.println("뻐꾹~");
  }
}

public class AnimalDemo {
  public static void main(String[] args) {
    Dog d = new Dog();
    Cuckoo c = new Cuckoo();
    
    makeSound(d);
    makeSound(c);
  }
  
  static void makeSound(Animal a) {     // Dog 객체나 Cuckoo 객체를 대입하면 Animal 타입으로 변환한다.
    a.sound();      // a 객체의 타입을 실행 도중에 결정한다.
  }                 // a 객체가 Dog 타입이면 '멍멍~~',
}                   // Cuckoo 타입이면 '뻐꾹~~'을 출력한다.
```

- 출력값

```
멍멍~~
뻑꾹~~
```

인터페이스 타입 변수에 대입된 구현 객체를 강제로 타입을 변환해서 구현 객체의 메서드를 호출하는 예제

- 인터페이스와 다형성 3

```java
interface Movable {
  void move(int x);
}

class Car implements Mobvable {
  private int pos = 0;
  
  public void move(int x) {
    pos += x;                   // Movable 인터페이스의 추상 메서드인 move()의 구현체이다.
  }
  
  public void show() {
    System.out.println(pos + "m 이동했습니다.");
  }
}

public class MovableDemo {
  public static void main(String[] args) {
    Movable m = new Car();
    
    m.move(5);
    // m.show();        // Movable 타입에는 show() 메서드가 없디 깨문에 호출할 수 없다.
    
    Car c = (Car)m;     // m이 참조하는 실제 객체가 Car 타입이므로 강제 타입 변환할 수 있다.
    c.move(10);
    c.show();       // Car 타입에는 show() 메서드가 있어 호출할 수 있다.
  }
}
```

- 출력값

```
15m 이동 했습니다.
```

위에서 강제 타입 변환을 그림으로 나타내면 다음과 같다.

![ex7-14](/assets/images/ex7-14.png)


