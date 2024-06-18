---
title:  "[Java] polymorphism 다형성" 
categories: Java
tags: [Java, Programming, coding]
toc: true
toc_sticky: true
date:  2024-06-18
last_modified_at:  2024-06-18
---

![java.png](/assets/images/java.png)

> # polymorphism (다형성)

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

**Animal 패키지**

```java
package section01.polymorphism;

public class Animal {
    public void eat(){
        System.out.println("동물이 먹이를 먹습니다");
    }

    public void run(){
        System.out.println("동물이 달려갑니다.");
    }

    public void cry(){
        System.out.println("동물이 먹습니다.");
    }
}
```

**Rabbit 패키지**

```java
package section01.polymorphism;

public class Rabbit extends Animal{
    @Override
    public void eat() {
        System.out.println("토끼가 풀을 뜯어먹고 있습니다.");
    }

    @Override
    public void run() {
        System.out.println("토끼가 달려갑니다. 깡총깡총!.");
    }

    @Override
    public void cry() {
        System.out.println("토끼가 울음소리를 냅니다. 끼익~ 끼익~");
    }

    public void jump(){
        System.out.println("토끼가 점프합니다 점프!");
    }
}
```

**Tiger 패키지**

```java
package section01.polymorphism;

public class Tiger extends Animal{

    @Override
    public void eat() {
        System.out.println("호랑이는 고리를 뜯어먹고있습니다.");
    }

    @Override
    public void run() {
        System.out.println("호랑이는 왠만하면 달리지 않습니다. 어슬렁~어슬렁~ 걸어갑니다.");
    }

    @Override
    public void cry() {
        System.out.println("호랑이가 고슴도치한테 처맞고 울고있습니다.");
    }

    public void bite(){
        System.out.println("호랑이가 물어뜯습니다..");
    }
}
```

**Application1**

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

출력값

```
동물이 먹이를 먹습니다
동물이 달려갑니다.
동물이 먹습니다.
======================================
토끼가 풀을 뜯어먹고 있습니다.
토끼가 달려갑니다. 깡총깡총!.
토끼가 울음소리를 냅니다. 끼익~ 끼익~
토끼가 점프합니다 점프!
======================================
호랑이는 고리를 뜯어먹고있습니다.
호랑이는 왠만하면 달리지 않습니다. 어슬렁~어슬렁~ 걸어갑니다.
호랑이가 고슴도치한테 처맞고 울고있습니다.
호랑이가 물어뜯습니다..
======================================
토끼가 울음소리를 냅니다. 끼익~ 끼익~
호랑이가 고슴도치한테 처맞고 울고있습니다.
=============타입 형변확 확인=============
토끼가 점프합니다 점프!
호랑이가 물어뜯습니다..
============instanceof============
a1이 Tiger 타입인지 확인 : false
a1이 Rabbit 타입인지 확인 : true
a1이 Animal 타입인지 확인 : true
a1이 Object 타입인지 확인 : true
토끼가 점프합니다 점프!
```

**Application2**

```java
package section01.polymorphism;

public class Application2 {
    public static void main(String[] args) {

        /* 다형성을 적용하여 객체 배열을 만들어 인스턴스 연속처리 할 수 있다. */

        Animal[] animals = new Animal[5];
        animals[0] = new Rabbit();
        animals[1] = new Tiger();
        animals[2] = new Rabbit();
        animals[3] = new Tiger();
        animals[4] = new Rabbit();

        /* Animal 클래스가 가지는 메서드를 오버라이딩한 메서드를 호출시 동적 바인딩을 이용할 수 있다. */
        for (int i = 0; i < animals.length; i++ ) {
            animals[i].cry();
        }

        for (int i = 0; i < animals.length; i++ ) {

            if(animals[i] instanceof Rabbit){
                ((Rabbit)animals[i]).jump();

            }else if(animals[i] instanceof Tiger){
                ((Tiger)animals[i]).bite();
            }else{
                System.out.println("호랑이나 토끼가 아닙니다.");
            }
        }


    }
}
```

출력값

```
토끼가 울음소리를 냅니다. 끼익~ 끼익~
호랑이가 고슴도치한테 처맞고 울고있습니다.
토끼가 울음소리를 냅니다. 끼익~ 끼익~
호랑이가 고슴도치한테 처맞고 울고있습니다.
토끼가 울음소리를 냅니다. 끼익~ 끼익~
토끼가 점프합니다 점프!
호랑이가 물어뜯습니다..
토끼가 점프합니다 점프!
호랑이가 물어뜯습니다..
토끼가 점프합니다 점프!
```

**Application3**

```java
package section01.polymorphism;

public class Application3 {

    public static void main(String[] args) {
        /* 다형성을 적용하여 매개변수에 활용할 수 있다. */
        /* 1. 하단에 feed() 메서드 작성 */
        /* 2. 하단에 feed() 메서드 호출*/
        Application3 app3 = new Application3();

        Animal animal1 = new Rabbit();
        Animal animal2 = new Tiger();

        app3.feed(animal1);
        app3.feed(animal2);

        Rabbit animal3 = new Rabbit();
        Tiger animal4 = new Tiger();

        app3.feed(animal3);
        app3.feed(animal4);     //묵시적 형변환

        app3.feed((Animal) animal3);
        app3.feed((Animal)  animal4);     //명시적 형변환

        app3.feed(new Rabbit());
        app3.feed(new Tiger());
    }
    public void feed(Animal animal){

        animal.eat();


    }

}
```

출력값

```
토끼가 풀을 뜯어먹고 있습니다.
호랑이는 고리를 뜯어먹고있습니다.
토끼가 풀을 뜯어먹고 있습니다.
호랑이는 고리를 뜯어먹고있습니다.
토끼가 풀을 뜯어먹고 있습니다.
호랑이는 고리를 뜯어먹고있습니다.
토끼가 풀을 뜯어먹고 있습니다.
호랑이는 고리를 뜯어먹고있습니다.
```

**Application4**

```java
package section01.polymorphism;

import java.util.Random;

public class Application4 {

    public static void main(String[] args) {
        /* 다형성을 적용하여 리턴타입을 활용할 수 있다. */
        /* 1. getRandomAnimal() 추가 */

        /* 2. getRandomAnimal() 호출 */
        Application4 app4 = new Application4();

        Animal randomAnimal = app4.getRandomAnimal();
        randomAnimal.cry();

    }

    public Animal getRandomAnimal(){
        int random = (int)(Math.random() *2);

        return random == 0? new Rabbit() : new Tiger();
    }
}
```

출력값

```
호랑이가 고슴도치한테 처맞고 울고있습니다.
```

---

> ## 요약

1. Animal, Rabbit, Tiger 클래스

 - Animal 클래스를 상속받는 Rabbit 과 Tiger 클래스를 정의한다
 - 각 클래스는 eat(), run(), cry() 메소드를 오버라이딩해서 토끼와 호랑이에 맞게 동작하도록 구현

2. Application1 클래스
 
 - main() 메소드에서 Animal, Rabbit, Tiger 객체를 생성하고 메소드를 호출해서 다형성을 확인한다
 - 부모 클래스 타입으로 자식 클래스의 객체를 참조할 수 있고, instanceof 연산자를 사용해서 객체의 타입을 확인

3. Application2 클래스

 - main() 메소드에서 Animal 배열을 생성하고 Rabbit 과 Tiger 객체를 저장한다
 - 배열의 각 객체를 반복문으로 순회하면서 cry() 메소드를 호출한다
 - instanceof 연산자를 사용하여 Rabbit과 Tiger의 추가 메소드를 호출한다

4. Application3 클래스

 - feed() 메소드를 생성해서 Animal 타입을 매개변수로 받는다
 - 다형성을 활용하여 Rabbit 과 Tiger 객체를 매개변수로 전달하여 eat() 메소드를 호출한다

5. Application4 클래스

 - getRandomAnimal() 메소드를 생성하여 무작위로 Rabbit 또는 Tiger 객체를 반환한다
 - getRandomAnimal() 을 호출해서 반환된 객체의 cry() 메소드를 호출한다

