---
title: "[Java] 5주차. 클래스"
categories: Java
tags: [Java, Programming, coding]
toc: true
toc_sticky: true
date: 2024-05-09
last_modified_at: 2024-05-09
---

![java.png](/assets/images/java.png)

# **클래스**

객체 지향 프로그래밍을 알기 위해서 제일 먼저 알아야 할 것은 당연히 `객체`이다. 객체랑 무엇일까??
자바 오라클 공식문서를 참고해보자

> Real-world objects share two characteristicd: They all have state and behavior.

현실의 물체들은 두가지 특징이 있다. 상태와 행동이다

> Identifying the state and behavior for real-world objects is a great way to begin thinking in terms of object-oriented programming.

현실 물체들의 `상태`와 `행동`을 파악하는 것은 객체 지향 프로그래밍을 생각하기에 아주 좋은 방법이다.

예를 들어, 노트북을 예를 들어보자. 노트북은 전원이 켜진 상태, 꺼진 상태 이렇게 두가지의 상태를 나타낼 수 있다.
또, '노트북이 켜진다','노트북이 꺼진다' 와 같은 행동이 나타나진다.

> Software objects are conceptually similar to real-world objects: they too consist of state and related behavior. An object stores its state in fields (variables in some programming languages) and exposes its behavior through methods (functions in some programming languages). Methods operate on an object's internal state and serve as the primary mechanism for object-to-object communication. Hiding internal state and requiring all interaction to be performed through an object's methods is known as data encapsulation — a fundamental principle of object-oriented programming.

소프트웨어 객체도 현실세계 물체들과 비슷하다. 상태가 있고 그와 관련된 행동이 있다. 객체는 fields(프로그래밍언어에서 변수)에 상태를 나타냈고 methods(몇몇 프로그래밍언어에서 함수)로 행동을
표현했다. Methods는 객체 내부 상태를 관리하고 객체간의 대화를 하는데에 있어서 주요 매커니즘이 된다.
내부 상태를 숨기고 메서드를 통해 모든 상호작용을 수행하도록 하는 것을 `data encapsulation` 이라고 한다. 객체 지향 프로그래밍의 기본 원칙이다.

객체지향 프로그래밍은 객체의 행동(메서드)를 통해 상태(변수), 더 나아가 모든 상호작용을 수행하도록하는
프로그래밍 방식을 말한다.

현실에서 어떤 노트북이 있다고 하자. 똑같은 모델인 노트북의 갯수는 셀 수 없이 많을 것이다. 이것들은 특정
설계도를 가지고 만들어진다. 이 설계도를 객체 지향 프로밍에선 클래스라고 한다.

> A class is the blueprint from which individual objects are created.

클래스는 개별 객체가 만들어지는 첫사진이다.

스타벅스에 가서 커피를 주문한다고 하자. 주문서는 다음과 같이 코드로 표현가능하다

```java
package class1;

public class ClassDemo1 {
  
  public static void main(String[] args) {
    String coffeeName1 ="카페 아메리카노";
    String coffeeName1Size = "벤티";
    int coffeeName1Price = 5500;
    int coffeeName1Quantity = 1;
    System.out.println("커피명 : " + coffeeName1 +
                        ", 사이즈 : " + coffName1Size +
                        ", 가격 : " + coffName1Price +
                        ", 수량 : " + coffeeName1Quantity);

    System.out.println("커피명 : " + coffeeName2 +
                        ", 사이즈 : " + coffeeName2Size +
                        ", 가격 : " + coffeeName2Price +
                        ", 수량 : " + coffeeName2Quantity);
    }
}
```

단체로 회사에서 30명이 산다고 상상해보자. 한명 한명 다 귀찮게 추가해줘야 한다. 그렇다면 배열로 표현해보자

```java
package class1;

public class ClassDemo2 {

    public static void main(String[] args) {
        String[] coffeeName = {"카페 아메리카노", "스타벅스 돌체 라떼"};
        String[] coffeeNameSize = {"벤티", "그란데"};
        int[] coffeeNamePrice = {5500, 6400};
        int[] coffeeNameQuantity = {1, 1};

        System.out.println("커피명: " + coffeeName[0] + 
        				", 사이즈: " + coffeeNameSize[0] + 
        				", 가격: " + coffeeNamePrice[0] + 
        				", 수량: " + coffeeNameQuantity[0]);

        System.out.println("커피명: " + coffeeName[1] + 
        				", 사이즈: " + coffeeNameSize[1] + 
        				", 가격: " + coffeeNamePrice[1] + 
        				", 수량: " + coffeeNameQuantity[1]);
    }

}
```

하지만 배열도 많은 사람들이 살 때의 경우엔 쉽지 않다. 만약 누가 주문을 취소하면 인덱스가 그 주문에
해당하는 인덱스의 값들을 지워야 되는데 헷갈리고 쉽지 않다. 그렇다면 그냥 아예 이 각각의 커피를 하나의 객체로 보면 어떻게 될까?

```java
package class1;

public class ClassDemo3 {

    public static void main(String[] args) {
        Coffee coffee1 = new Coffee();
        coffee1.coffeeName = "카페 아메리카노";
        coffee1.coffeeNameSize = "벤티";
        coffee1.coffeeNamePrice = 5500;
        coffee1.coffeeNameQuantity = 1;

        Coffee coffee2 = new Coffee();
        coffee2.coffeeName = "스타벅스 돌체 라떼";
        coffee2.coffeeNameSize = "그란데";
        coffee2.coffeeNamePrice = 6400;
        coffee2.coffeeNameQuantity = 1;

        System.out.println("커피명: " + coffee1.coffeeName + 
        				", 사이즈: " + coffee1.coffeeNameSize + 
                        ", 가격: " + coffee1.coffeeNamePrice + 
                        ", 수량: " + coffee1.coffeeNameQuantity);

        System.out.println("커피명: " + coffee2.coffeeName + 
        				", 사이즈: " + coffee2.coffeeNameSize + 
        				", 가격: " + coffee2.coffeeNamePrice + 
        				", 수량: " + coffee2.coffeeNameQuantity);
    }

}

class Coffee {

    String coffeeName;
    String coffeeNameSize;
    int coffeeNamePrice;
    int coffeeNameQuantity;

}
```

눈으로 봐도 개별로 관리하기 용이해 진다는걸 알 수 있다.

참고로 `Coffee class`는 완성된 `application`이 아니기 때문에 `main method`에 포함되지 않는다. `application`에 사용되는 청사진(설계도)일 뿐이다.

## 클래스를 정의하는 법

클래스는 다음과 같은 방법으로 정의한다.

```java
class MyClass {
  // field, constructor, and
  // method declarations
}
```

> This is a class declaration. The class body (the area between the braces) contains all the code that provides for the life cycle of the objects created from the class: constructors for initializing new objects, declarations for the fields that provide the state of the class and its objects, and methods to implement the behavior of the class and its objects.

또한, public, private와 같은 modifiers를 class선언에 포함시켜 MyClass에 다른 클래스가 접근할 수 있는지를 결정짓는다. 
이 때, 두 가지 access level이 있다. `The Java™ Tutorials - Controlling Access to Members of a Class`참고

- top level: public, package-private
- member level: public, private, protected, package-private
- 
top-level에서의 modifier
여기서 top-level은 흔히 아는 한 class파일 안에서 가장 바깥 쪽에 정의하는 class를 뜻한다.

public
public으로 선언된 클래스는 어디에서든 접근 가능하다.

package-private
package-private는 클래스에 modifier가 없는 경우인데 이 때는 같은 package안에서만 클래스가 접근이 가능해진다.

member-level에서의 modifier
member variable에 접근가능 수준을 얘기한다.

public과 package-private는 top-level과 접근 수준이 같다. 나머지를 살펴보자.

protected
가장 특이한 녀석이다. 같은 패키지내에서 볼 수 있고, 다른 패키지에서는 해당 클래스의 subclass에 의해서도 가능해진다.

private
같은 클래스 내에서만 멤버에 접근가능하다.

클래스 선언은 새로운 클래스를 정의하고 구현 방법을 설명한다.

## 객체 만드는 법 (new 키워드 이해하기)

클래스는 객체의 청사진이기 때문에 객체를 만드려면 클래스로부터 만들어야 한다. 다음은 자바 오라클 공식문서 예제이다. 변수명만 살짝 바꿨다.

```java
public class Point {

    public int x = 0;
    public int y = 0;

    // 생성자
    public Point(int a, int b) {
        x = a;
        y = b;
    }

}
```
```java
public class Rectangle {

    public int width = 0;
    public int height = 0;
    public Point origin;

    public Rectangle() {
        origin = new Point(0, 0);
    }

    public Rectangle(Point origin) {
        this.origin = origin;
    }

    public Rectangle(int width, int height) {
        this.width = width;
        this.height = height;
    }

    public Rectangle( Point origin, int width, int height) {
        this.width = width;
        this.height = height;
        this.origin = origin;
    }

    public void move(int x, int y) {
        origin.x = x;
        origin.y = y;
    }

    public int getArea() {
        return width * height;
    }

}
```
```java
public class CreateObjectDemo {

    public static void main(String[] args) {

        Point originOne = new Point(23, 94);
        Rectangle rectangleOne = new Rectangle(originOne, 100, 200);
        Rectangle rectangleTwo = new Rectangle(50, 100);

        System.out.println("rectangleOne.width = " + rectangleOne.width);
        System.out.println("rectangleOne.height = " + rectangleOne.height);
        System.out.println("rectangleOne.getArea() = " + rectangleOne.getArea());

        System.out.println(rectangleTwo.origin); //null
        //System.out.println("rectangleTwo.origin.x = " + rectangleTwo.origin.x);
        //System.out.println("rectangleTwo.origin.y = " + rectangleTwo.origin.y);

        rectangleTwo.origin = originOne;

        System.out.println("rectangleTwo.origin.x = " + rectangleTwo.origin.x);
        System.out.println("rectangleTwo.origin.y = " + rectangleTwo.origin.y);

        rectangleTwo.move(40, 72);
        System.out.println("rectangleTwo.origin.x = " + rectangleTwo.origin.x);
        System.out.println("rectangleTwo.origin.y = " + rectangleTwo.origin.y);

    }

}
```

```java
Point originOne = new Point(23, 94);
Rectangle rectangleOne = new Rectangle(originOne, 100, 200);
Rectangle rectangleTwo = new Rectangle(50, 100);
```

객체를 생성할 때 위와 같이 나타내는데 세부분으로 나눈다

> 1. Declaration: The code set in bold are all variable declarations that associate a variable name with an object type.
> 2. Instantiation: The new keyword is a Java operator that creates the object.
> 3. Initialization: The new operator is followed by a call to a constructor, which initializes the new object.

> 1. 선언 : 오브젝트 타입과 변수 이름을 연결시키는 변수 선언
> 2. 인스턴스화 : new 키워드는 Java연산자로 object를 생성한다
> 3. 초기화 : new 연산자 다음에는 생성자를 호출하여 새로운 객체를 초기화한다

## 객체를 참조하는 변수 선언하기

```
type name;
```

변수를 선언할 땐 다음과 같이 선언한다. 이것은 컴파일러에게 타입이 type 인 데이터를 참조할 때 name 을 사용한다는 사실을 알린다

```
Point originOne;
```
Object 타입일 때도 다음과 같이 선언한다. 그냥 이렇게 originOne(참조변수)만 선언되어 있으면 그 값이 결정이 되지 않는다.
코드로 사용하기 위해선 반드시 new 연산자를 통해 객체를 생성하고 originOne 에 할당시켜줘야 한다

## 클래스 인스턴스화 하기

new 연산자를 통해 새 객체에 대한 메모리를 할당하고 해당 메모리에 대한 참조를 반환하여 클래스를 인스턴스화한다. 여기서 인스턴스화 한다라는 말은 객체를 생성한다는 말과 같다. 객체를 생성하면 클래스의 인스턴스를 만드는 것이므로 클래스를 인스턴스화한다.

new 연산자는 하나의 후위인자가 필요하다. 즉, 생성자 호출이 필요하다. 생성자의 이름은 인스턴스화할 클래스 이름을 제공한다.

```java
Point originOne = new Point(23, 94);
```

new 연산자는 생성된 객체에 대한 참조를 반환한다. 이 참조는 위와 같이 적절한 타입의 변수에 할당된다.

```java
int height = new Rectangle().height;
```
```java
int valueX = new Point(2, 3).x;
int valueY = new Point(2, 3).y;
        
System.out.println("valueX = " + valueX); //2
System.out.println("valueY = " + valueY); //3
```

위와 같이 new연산자는 변수에 할당을 하는데 안쓰일 수도 있다. 표현식에 직접적으로 사용할 수도 있다.


## 객체 초기화 하기

```java
public class Point {
    public int x = 0;
    public int y = 0;
    //생성자
    public Point(int a, int b) {
        x = a;
        y = b;
    }
}
```

이 클래스는 생성자가 하나 있음을 알 수 있다. 먼저 매서드명이 클래스명과 동일하다. 그리고 return 값이 없다. Point 클래스의 생성자는 코드에서 선언한대로 두 개의 정수 arguments를 받는다. 다음 문에서는 23과 94의 값으로 arguments를 준다.

```java
Point originOne = new Point(23, 94);
```

Rectangle class를 보면 4개의 생성자가 있는 것을 볼 수 있다. 그리고 각각, width, height, origin을 제공한다.

Rectangle class는 4개의 생성자를 가지고 있다.

```java
public class Rectangle {
    public int width = 0;
    public int height = 0;
    public Point origin;

    // four constructors
    public Rectangle() {
        origin = new Point(0, 0);
    }
    public Rectangle(Point p) {
        origin = p;
    }
    public Rectangle(int w, int h) {
        origin = new Point(0, 0);
        width = w;
        height = h;
    }
    public Rectangle(Point p, int w, int h) {
        origin = p;
        width = w;
        height = h;
    }

    // a method for moving the rectangle
    public void move(int x, int y) {
        origin.x = x;
        origin.y = y;
    }

    // a method for computing the area of the rectangle
    public int getArea() {
        return width * height;
    }
}
```
생성자들은 각각 다른 시그니처들을 갖는다. The Java compiler는 arguments의 갯수와 타입에 따라 생성자를 구분한다. Java 컴파일러는 다음의 코드를 발견하면, Point 인수와 두 개의 정수 인수가 뒤따르는 Rectangle 클래스의 생성자를 호출해야 한다는 것을 알고 있다.

```java
Rectangle rectangleOne = new Rectangle(originOne, 100, 200);
```

이렇게 하면 Rectangle의 생성자 중 하나를 호출하여 origin을 originOne으로 초기화한다. 또, width는 100, height는 200으로 설정된다.

```java
Rectangle rectangleTwo = new Rectangle(50, 100);
```

위의 코드는 Rectangle 생성자를 호출한다. 위의 Rectangle(int width, int height)를 보면 알겠지만 x와 y의 값이 0인 new Point객체를 생성한다

```java
Rectangle rectangle = new Rectangl();
```

위의 코드는 아규먼트가 아예 없다. 이것은 no-argument constructor라고 한다.

모든 클래스들이 적어도 하나이상 생성자를 갖는다. 만약 아무 생성자가 없으면 the Java compiler가 자동으로 no-argument constructor를 제공하고 이것을 default constructor라고 불린다. 이 dafault constructor는 부모 클래스의 no-argument constructor를 호출하거나 부모 클래스가 없는경우 Object 생성자를 호출한다. 만약 부모가 생성자가 없으면 컴파일러는 프로그램을 거부한다.

이러한 현상을 막기 위해 Java의 모든 클래스엔 프로그래머가 명시적으로 선언했거나 Java 컴파일러가 자동으로 생성자를 제공한다.

## 객체 사용하기

객체의 field 참조하기

```
objectReference.fieldName
```

객체의 클래스 밖에 있는 코드는 이렇게 객체 참조 또는 점(.) 연산자를 사용하고 그 뒤에 간단한 이름을 사용해야 한다.

예를 들어, CreateObjectDemo class의 코드는 Rectangle class 코드 외부에 있다. 따라서, rectOne이라는 Rectangle 객체 내의 origin, width, height field를 참조하려면, 각각CreateObjectDemo class는 rectOne.origin, rectOne.width, rectOne.height란 이름을 사용해야 한다. 프로그램은 이 이름 중 두 개를 사용하여 rectOne width와 height를 나타낸다.

```java
System.out.println("Width of rectOne: "  + rectOne.width);
System.out.println("Height of rectOne: " + rectOne.height);
```

> Attempting to use the simple names width and height from the code in the CreateObjectDemo class doesn't make sense — those fields exist only within an object — and results in a compiler error.

CreateObjectDemo class 안의 코드에서 단순한 이름 width나 height를 사용하려 할 때 해당 field는 객체 내에서만 존재하므로 의미가 없고 컴파일 에러가 발생한다.

new 연산자는 객체의 참조를 반환하기 때문에 다음과 같은 문도 가능하다.

```java
int height = new Rectangle().height;
```

이 프로그램이 실행된 후에는 참조를 어디에도 저장하지 않았기 때문에 Rectangle에 대한 참조가 더 이상 존재하지 않게 된다. 해당 리소스는 JVM에서 자유롭게 재활용 가능하다.

## 객체의 메서드 호출

```java
objectReference.methodName(argumentList);
```
```java
objectReference.methodName();
```

위와 같이 점연산자를 사용하여 메서드를 호출한다. 그리고 괄호안에 인자를 넣을 수 있고, 인자가 필요없다면 빈칸으로 써도 된다.

그리고 필드를 참조했을 때와 마찬가지로 new연산자를 써서 참조를 반환하고 그 new 객체의 메서드로부터 값을 반환하게 할 수 있다

```java
new Rectangle(100, 50).getArea()
```

getArea()와 같은 메서드는 값을 반환한다. 값을 바환하는 메서드의 경우, 메서드 호출을 사용할 수 있다.
다음 코드에서는 getArea()가 areaOfRectangle 변수에 할당이 된다

```java
int areaOfRectangle = new Rectangle(100, 50).getArea();
```


> Remember, invoking a method on a particular object is the same as sending a message to that object. In this case, the object that getArea() is invoked on is the rectangle returned by the constructor.


특정 객체의 메서드를 호출하는건 객체에게 메시지를 보내는 것과 같다. 이 경우에, getArea()가 호출되는 객체는 생성자가 반환하는 retangle이다.

## 메서드 정의하는 법

`The Java™ Tutorials`의 Defining Methods를 참고
자바에서 메서드를 다음 코드처럼 정의한다.

```java
public int add(int a, int b) {
  return a + b;
}
```

method declaration의 필수 요소에는 리턴타입, 메서드 이름, 괄호(), 바디{}가 있다.

더 일반적으로 6개 구성요소가 있다:

1. Modifiers<br>
  public, private, static같은 걸 말한다.
2. The return type<br>
리턴값의 타입 또는 리턴값이 없을 때 void
3. 메서드 이름<br>
필드 이름과 비슷하다. 그러나, 살짝 다르다.
4. 괄호안의 파라미터<br>
파라미터가 없는 경우엔 빈칸으로 남긴다.
5. An exception list<br>
6. braces 사이의 메서드 바디<br>
메서드 코드들이 들어가고 지역변수의 선언이 포함된다.

위의 코드에서 add(int a, int b)를 method signature라고 한다. 메서드이름과 파라미터 타입, 이렇게 메서드 선언에서의 두 개의 구성요소로 이루어져 있다.

## Overloading Methods

> The Java programming language supports overloading methods, and Java can distinguish between methods with different method signatures. This means that methods within a class can have the same name if they have different parameter lists (there are some qualifications to this that will be discussed in the lesson titled "Interfaces and Inheritance").

메서드 오버로딩을 지원한다. Java 는 서로 다른 메서드 시그니처로 구별한다. 클래스안에 메서드명이 같아도 파라미터 리스트가 다를 수 있다

> You cannot declare more than one method with the same name and the same number and type of arguments, because the compiler cannot tell them apart.

같은 메서드명과 같은 수의 인자 타입을 가진 메서드를 한 개 이상 선언할 수 없는데, 컴파일러가 구별하지 못하기 떄문이다

> The compiler does not consider return type when differentiating methods, so you cannot declare two methods with the same signature even if they have a different return type.

컴파일러는 메서드를 구분할때 리턴타입은 신경안쓰기 떄문에 만약 리턴타입이 다르더라도 같은 시그니처의 메서드 두개를 선언할 수 없다

## 생성자 정의하는법

`The Java™ Tutorials`의 Providing Constructors for Your Classes 참고
클래스에는 클래스 청사진으로부터 객체를 만들기 위한 생성자가 포함되어 있다. 생성자 선언은 메서드 선언과 비슷하게 보인다. 하지만, 생성자는 클래스의 이름을 사용하고 리턴타입이 없다. 예를 들어, Car는 한 생성자가 있다.

```java
public Car(int price, int speed, int gear) {
  price = standardPrice;
  speed = starSpeed;
  gear = starGear;
}
```

람보르기니라고 불리는 new Car 객체를 생성하고, new 연산자로 생성자를 호출해본다

```java
Car lamborghini = new Car(200000000, 0, 8);
```

`new Car(200000000, 0, 8)` 는 메모리에 객체를 위한 공간을 생성하도 필드를 초기화 한다.

Car 클래스가 오직 하나의 생성자만 갖고있더라도 no-argument constructor 를 포함하여 다른 생성자를 가질 수 있다

```java
public Car() {
	price = 30000000
    speed = 0
    gear = 6
}
```

`Car myCar = new Car();` 는 no-argument constructor를 호출하여 myCar라는 새로운 Car객체를 생성한다.

다른 argument 리스트기 때문에 위의 생성자는 선언되어질 수 있다. 메서드와 마찬가지로 the Java platform은 argument수와 타입에 따라 생성자를 구분한다. 만약 같은 수와 같은 타입의 생성자를 두개 만들어버리면 구분을 할 수 없기 때문에 컴파일 타임 에러가 난다.

> You don't have to provide any constructors for your class, but you must be careful when doing this.

클래스에 어느 생성자를 제공할 필요는 없지만, 조심해야 된다.

> The compiler automatically provides a no-argument, default constructor for any class without constructors. This default constructor will call the no-argument constructor of the superclass.

