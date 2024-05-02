---
title:  "[Java] 상속" 
categories: Java
tags: [Java, Programming, coding]
toc: true
toc_sticky: true
date:  2024-06-15
last_modified_at:  2024-06-15
---

![java.png](/assets/images/java.png)

> ### 상속에 이란??

- 상속은 현실 세계 상속과 비슷한 개념이다
- 부모가 가지고 있는 재산(자바에서는 클래스가 가지는 맴버)을 자식이 물려받는 의미이다
- 클래스 또한 부모 클래스와 자식 클래스로 역할을 나누어서 부모가 가지는 맴버를 자식이 물려받아 자기의 맴버인 것 처럼 사용할 수 있도록 만든 기술이다
- 단순 물려받는 개념보다 조금 더 나아간다면 자바에서의 상속은 부모 클래스의 확장(extend)의 개념을 가진다
- 물려 받아서 자신의 것처럼 사용하는 것 뿐만 아니라 추가적인 맴버도 작성이 가능하다
- 특히 메소드 재정의(overriding)라는 기술을 이용해서 부모가 가진 메소드를 재정의하는 것도 가능하다

> ### 메소드 재정의(overriding)이란??

- 부모가 가지는 메소드 선언부를 그대로 사용하면서 자식 클래스가 정의한 메소드대로 동작하도록 구현 몸체 부분을 새롭게 다시 작성하는 기술이다
- 메소드 재정의를 하면 메소드를 호출할 시 재정의한 메소드가 우선으로 동작하게 된다
- 이러한 사송이라는 기술을 사용하게 되면 얻게되는 이점은 두가지가 있다
1. 새로운 클래스를 작성시 기존에 작성한 클래스를 재사용 할 수 있다
2. 재사용 시 생산성을 크게 향상시킬 수 있다(새롭게 작성하는 것 보다 빠르다)
3. 공통적으로 사용하는 코드가 부모클래스에 존재하면 수정사항이 생길 시 부모 클래스만 수정해도 전체적으로 적용된다(유지 보수성 증가)
4. 클래스간의 계층 관계가 형성되며 다형성의 문법적인 토대가 된다

---

상속으로 인한 단점

1. 부모클래스의 기능을 추가/변경시에 자식클래스가 정상 동작하는지 예측이 힘들다
2. 상속 구조가 복잡해질 수록 그 영향에 대한 예측이 힘들어 이전 단점이 유지보수성이 증가한다는 장점과는 반대로 유지보수에 악영향을 미친다
3. 또한 부모클래스 변경 또한 쉽지 않다. 자식 클래스에서 중요하게 사용하는 기능인 경우 부모클래스 변경할 시 자식 클래스에 모두 영향을 줄 수 있다. 역시 유지보수에 악영향을 미친다
4. 부모클래스에서는 의미있었던 기능들이 자식 클래스에서는 무의미 할 수 있다(불필요한 기능이 추가됨)

장점과 단점을 고려했을 때 상속은 재사용이라는 장점만을 바라보게 되면 오용의 가능성이 있기 때문에 유지보수에 좋지 않은 코드를 작성할 확률이 높다<br/>
 상속은 IS-A 관계로 구분되는 경우에만 사용해야 한다

---

객체지향 설계 관점에서 바라보는 상속

- 모든 객체는 자신이 수신한 메세지에 대한 응답을 해야하는 책임을 가지고, 그 책임의 규모는 적절해야 한다
- 적절한 책임을 가진 객체들이 서로 협력(메세지 수신과 응답)을 통해 프로그램이 동작하는 것을 객체지향 프로그램이라고 한다
- 적절한 책임을 수행하는 객체 또한 그 객체만 수행할 수 있는 기능이라기 보다 역할을 관점으로 바라봐야한다
- 역할이란 동일한 동작을 수행하는  것을 정의한 것이며, 대체 가능성을 의미한다.
- 부모 클래스를 추상화하는 경우 역할의 관점으로 바라봐야한다
- 그래야 자식클래스로 생성한 객체들이 서로 역할을 수행해가며 유연한 코드를 작성할 수 있게 된다
- 동일한 역할을 가지는 모든 객체는 동일한 메세지를 수신하기는 하지만 객체별로 그 메시지에 응답하는 방식이 서로 다를 수 있다

---

예제를 만들어 연습해보자 Car 클래스를 상속하고있는 FireCar 와 RacingCar

```java
package section01.extend;

public class Application {
    public static void main(String[] args) {

        Car car = new Car();
        car.soundHorn();
        car.run();
        car.soundHorn();
        car.stop();
        car.soundHorn();

        FireCar fireCar = new FireCar();
        fireCar.soundHorn();
        fireCar.run();
        fireCar.soundHorn();
        fireCar.stop();
        fireCar.soundHorn();

        fireCar.sprayWater();

        RacingCar racingCar = new RacingCar();
        racingCar.soundHorn();
        racingCar.run();
        racingCar.soundHorn();
        racingCar.stop();
        racingCar.soundHorn();

    }
}
```
```java
package section01.extend;

public class Car {
  
    private boolean runningStatus;

    public Car(){
        System.out.println("Car 클레스 기본 생성자 호출됨.....");
    }

    public void run(){
        runningStatus = true;
        System.out.println("자동차가 달립니다~");
    }

    public void soundHorn() {
        if(isRunning()) {
            System.out.println("빵!빵!");
        }else{
            System.out.println("주행 중이 아닌 상태에서는 경적을 울릴 수 없습니다.");
        }
    }
    //private boolean isRunning(){
        protected boolean isRunning(){
        return runningStatus;
    }

    public void stop(){

        runningStatus = false;
        System.out.println("자동차가 멈춥니다.");
    }

}
```
```java
package section01.extend;

public class FireCar extends Car {

    public FireCar() {

        super();

        System.out.println("FireCar 클래스의 기본 생성자 호출됨");

    }

    @Override
    public void soundHorn() {

        if (isRunning()) {
            System.out.println("빠아아아아아앙!!!!!!! 빵!!");
        } else {
            System.out.println("소방차가 앞으로 갈 수 없습니다 비키세요 비켜!!");
        }
    }
        public void sprayWater() {

            System.out.println("불난 곳을 발견했습니다. 물을 뿌립니다 ===========");
        }
    }
```
```java
package section01.extend;

public class RacingCar extends Car {

    public RacingCar(){
        System.out.println("RacingCar 클레스 기본 생성자 호출됨 ");
    }

    @Override
    public  void run() {

        System.out.println("레이싱카가 전속력으로 질주합니다!!!");
    }

    @Override
    public  void soundHorn() {

        System.out.println("레이싱카는 경적을 울리지 않습니다. (조용.....)");
    }

    @Override
    public void stop() {

        System.out.println("레이싱카가 멈춥니다.");
    }
}
```

---

출력 값

```
Car 클레스 기본 생성자 호출됨.....
주행 중이 아닌 상태에서는 경적을 울릴 수 없습니다.
자동차가 달립니다~
빵!빵!
자동차가 멈춥니다.
주행 중이 아닌 상태에서는 경적을 울릴 수 없습니다.
Car 클레스 기본 생성자 호출됨.....
FireCar 클래스의 기본 생성자 호출됨
소방차가 앞으로 갈 수 없습니다 비키세요 비켜!!
자동차가 달립니다~
빠아아아아아앙!!!!!!! 빵!!
자동차가 멈춥니다.
소방차가 앞으로 갈 수 없습니다 비키세요 비켜!!
불난 곳을 발견했습니다. 물을 뿌립니다 ===========
Car 클레스 기본 생성자 호출됨.....
RacingCar 클레스 기본 생성자 호출됨 
레이싱카는 경적을 울리지 않습니다. (조용.....)
레이싱카가 전속력으로 질주합니다!!!
레이싱카는 경적을 울리지 않습니다. (조용.....)
레이싱카가 멈춥니다.
레이싱카는 경적을 울리지 않습니다. (조용.....)
```

> 코드리뷰

1. **상속관계** : 'FireCar' 와 'RacingCar' 클래스가 'Car' 클래스를 상속하고 있다. 기본적인 상속의 예이다
2. **생성자 호출** : 각 클래스의 생성자가 호출될 때 출력문이 실행되어 생성자가 호출되는 것을 확인할 수 있다. 'super()'를 사용해서 부모 클래스의 생성자를 명시적으로 호출하는 것도 볼 수 있다
3. **super** : 부모 클래스의 생서자를 호출할때 사용된다. 자식 클스가 부모 클래스의 필드를 초기화하거나 부모클래스의 초기화 코드를 실행할 수 있다
4. **메소드 오버라이딩** :  'soundHorn()' 및 'run()' 메소드가 서브클래스에서 오버라이드되어 부모 클래스의 동작을 변경하고 있다. 다형성의 예시이다
5. **보호된 멤버** : 'isRunning()'메소드가 'protected' 로 선언되어 하위 클래스에서도 접근할 수 있도록 되어 있다
6. **다형성** : 'Car' 클래스 타입의 변수로 'Car', 'FireCar','RacingCar' 객체를 모두 다루고 있다.
7. **기능 확장** : 'FireCar' 클래스에서는 'sprayWater()' 메소드가 추가되어있다. 자식 클래스에서 부모 클래스의 기능을 확장하는 방법이다
8. **출력** : 각 객체의 메소드 호출 결과에 따라 다른 출력이 표시된다

---

### 요약.

객체 지향 프로그래밍의 여러 개념을 보여주고있고, 잘 작성되서 클래스 간의 관계와 상속, 다형성 등을 명확하게 보여주고 있다
