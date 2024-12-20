---
title: "[Java] 1주차. VM과 자바 코드"
categories: Java
tags:
  - Java
  - Programming
  - coding
toc: true
toc_sticky: true
date: 2024-04-20
last_modified_at: 2024-04-20
---

![java.png](/assets/images/java.png)

# **JVM이란 무엇인가?**

Java Virtual Machine의 줄임말

직역하면 자바를 실행하기 위한 가상 기계(컴퓨터)라고 할 수 있다

Java 는 OS에 종속적이지 않다는 특징을 가지고 있다. OS에 종속받지 않고 실행되기 위해선 OS 위에서 Java를 실행시킬 무언가가 필요하다. 그게 바로 JVM 이다.

즉, OS에 종속받지 않고 CPU가 Java를 인식, 실행할 수 있게 하는 가상 컴퓨터이다

![컴파일 과정](/assets/images/compiler.png)

Java 소스코드, 즉 원시코드(*.java)는 CPU가 인식을 하지 못하므로 기계어로 컴파일을 해줘야한다 <BR/>
하지만 Java는 JVM이라는 가상 머신을 거쳐서 OS에 도달하기 때문에 OS가 인식할 수 있는 기계어로 바로 컴파일 되는게 아니라 JVM이 인식할 수 있는 Java bytecode(*.class)로 변환된다

Java compiler 가 .java 파일을 .class 라는 Java bytecode 로 변환한다.

```
여기서 Java comepiler는 JDK 를 설치하면 bin 에 존재하는 javac.exe를 말한다.(즉, JDK에 Java compiler가 포함되어 있다는 소리) javac 명령어를 통해 .java를 .class로 컴파일 할 수 있다
```

변환된 bytecode는 기계어가 아니기 때문에 OS에서 바로 실행되지 않는다

이 때, JVM 이 OS가 bytecode 를 이해할 수 있도록 해석해준다. 따라서 Byte Code 는 JVM 위에서 OS 상관없이 실행될 수 있는 것이다

OS에 종속적이지 않고, Java 파일 하나만 만들면 어느 디바이스든 JVM 위에서 실행할 수 있다

---

# 컴파일 하는 방법

아래는 Java Compiler 에 의해 .java 파일을 .class 라는 Java bytecode 로 만드는 과정이다

Java Compiler 는 JDK를 설치하면 javac.exe 라는 실행 파일 형태로 설치된다. 정확히는  JDK 의 bin 폴더에 javac.exe로 존재한다

Java Complier 의 javac 라는 명령어를 사용하면 .class 파일을 생성할 수 있다

> 예제

```java
pulic class test {
	public static void main(String[] args) {
		System.out.println("Hello World");
	}
}
```

"Hello World" 를 출력하는 .java 파일을 생성하고 이를 .class 파일로 변환시켜보자

```bash
c:\Users\owner>cd Desktop
```

Windows 를 기준으로, cmd 창을 열고 해당 .java 파일이 있는 곳으로 이동한다.

```makefile
c:\Users\owner\Desktop\javac test.java
```

해당 위치(바탕화면)에 .class 파일이 생성된걸 확인할 수 있다

---

# 실행하는 방법

예제
<br/>

java 명령어로 .class 파일을 실행 시킬 수 있다

```
JDK 디렉토리의 /bin 폴더에 존재하는 java.exe 는 JVM을 구동시키기 위한 명령 프로그램이다.
(.JRE)
java 명령어로 JVM 을 실행시킬 수 있다
```

.class 파일이 위치한 곳으로 이동 후 java <.class  파일 이름> 을 입력해 실행시킨다

```bash
C:|Users|owner>cd Destop
C:|Users|owner|Desktop>java test
Hello World
```

"Hello World"가 출력되면서 test.class 파일이 실행된 걸 확인할 수 있다

---

# 바이코드란 무엇인가?

가상 컴퓨터(VM)에서 돌아가는 실행 프로그램을 위한 이진 표현법<br/>

자바 바이트 코드(Java bytecode)는 JVM 이 이해할 수 있는 언어로 변환된 자바 소스코드를 의미한다. 자바 컴파일러에 의해 변환된 코드의 명령어 크기가 1바이트라서 자바 바이트 코드라고 불린다<br/>

바이트 코드는 다시 실시간 번역기 또는 JIT 컴파일러에 의해 바이너리 코드로 변환된다<br/>

## 바이너리 코드란?

- 바이너리 코드 또는 이진 코드라고 함
- 컴퓨터가 인식할 수 있는 0과 1로 구성된 이진코드

## 기계어란?

- 0과 1로 이루어진 바이너리 코드이다.
- 기계어가 이진코드로 이루어졌을 뿐 모든 이진코드가 기계어인 것은 아니다
- 기계어는 특정한 언어가 아니라 CPU 가 이해하는 명령어 집합이며, CPU 제조사마다 기계어가 다를 수 있다

즉, CPU가 이해하는 언어는 바이너리 코드, 가상 머신이 이해하는 코드는 바이트 코드 이다

---

# JIT 컴파일러란 무엇이며 어떻게 동작하는가

JIT 컴파일(just-in-time compliation) 또는 동적 번역(dynamic translation) 이라고 한다<br/>

JIT 컴파일러는 프로그램을 실제 실행하는 시점에 기계어로 번역하는 컴파일러이다<br/>

인터프리터 방식의 단점을 보완하기 위해 도입되었다<br/>

`인터프리터 방식으로 실행하다가 적절한 시점에 바이트 코드 전체를 컴파일하여 기계어로 변경하고, 이후에는 더 이상 인터프리팅 하지 않고 기계어로 직접 실행하는 방식이다`<br/>

기계어(컴파일된 코드)는 캐시에 보관하기 때문에 한 번 컴파일된 코드는 빠르게 수행하게 된다. 물론 JIT 컴파일러가 컴파일 하는 과정은 바이트 코드를 인터프리팅 하는 것보다 훨신 오래걸리므로 한 번만 실행되는 코드라면 컴파일 하지 않고 인터프리팅하는 것이 유리하다.<br/>

따라서 JIT 컴파일러를 사용하는 JVM 들은 내부적으로 해당 메서드가 얼마나 자주 수행되는지 체크하고 일정 정도를 넣을때에만 컴파일을 수행한다<br/>

자바에선 자바 컴파일러가 자바 프로그램 코드를 바이트 코드로 변환한 다음, 실제 바이트 코드를 실행하는 시점에서 자바 가상 머신(JVM, 정확히는 JRE)이 바이트 코드를 JIT 컴파일을 통해 기계어로 변환한다<br/>

---

# JVM 구성요소

![JVM 구성요소](/assets/images/JVM.png)

JVM은 크게 아래와 같이 이루어져 있다

- 클래스 로더(Class Loader)
- 실행 엔진(Execution Engine)
  - 인터프리터(Interpreter)
  - JIT 컴파일러(Just-in-Time)
  - 가비지 콜렉터(Garbage collector)
- 런타임 데이터 영역(Runtime Data Area)

클래스 로더<br/>

JVM 내로 클래스 파일 (*.class)을 로드하고, 링크를 통해 배치하는 작업을 수행하는 모듈이다 런 타임시 동적으로 클래스를 로드하고 jar 파일 내 저장된 클래스들을 JVM 위에 탑재한다. 즉, 틀래스를 처음으로 참조할 때, 해당 클래스를 로드하고 링크하는 역할을 한다

실행 엔진<br/>

클래스를 실행시키는 역할이다 <br/>

클래스 로더가 JVM내의 런타임 데이터 영역에 바이트 코드를 배치시키고, 이것은 실행 엔진에 의해 실행된다 <br/>

자바 바이트 코드(*.class)는 기계가 바로 수행할 수 있는 언어보다는 비교적 인간이 보기 편한 형태로 기술된 것이다. 그래서 실행 엔진은 이와 같은 바이트 코드를 실제로 JVM 내부에서 기계가 실행 할 수 잇는 형태로 변경한다

인터프리터<br/>

실행 엔진은 자바 바이트 코드를 명령어 단위로 읽어서 실행한다 <br/>

하지만 한 줄씩 수행하기 때문에 느리다는 단점이 있다<br/>

JIT(Just-In-Time)<br/>

인터프리터 방식으로 실행하다가 적절한 시점에 바이트 코드 전체를 컴파일하여 기계어로 변경하고,<br/>

이후에는 더 이상 인터프리팅 하지 않고 기계어로 직접 실행하는 방식이다<br/>

가비지 콜렉터<br/>

더이상 사용되지 않는 인스턴스를 찾아 메모리에서 삭제함<br/>

Runtime Data Area<br/>

![Runtime Area](/assets/images/runtimearea.png)<br/>

프로그램을 수행하기 위해 os에서 할당받은 메모리 공간<br/>

PC Register<br/>

Thread 가 시작될 때 생성되며 생성될 때마다 생성되는 공간으로, 스레드마다 하나씩 존재한다 Thread 가 어떤 부분을 어떤 명령으로 실행해야 할 지에 대한 기록을 하는 부분으로 현재 수행 중인 JVM 명령의 주소를 갖는다<br/>

## 프로세스(process)란?

- 단순히 실행 중인 프로그램(program)
- 즉, 사용자가 작성한 프로그램이 운영체제에 의해 메모리 공간을 할당받아 실행 중인 것을 만한다
- 이러한 프로세스는 프로그램에 사용되는 '데이터와 메모리 등의 자원 그리고 스레드로 구성된다'<br/>

## 스레드(thread)란?

- 스레드(thread)란 프로세스( process)내에서 실제로 작업을 수행하는 주체를 의미
- 모든 프로세스에는 한 개 이상의 스레드가 존재하여 작업을 수행한다
- 또한, 두 개 이상의 스레드를 가지는 프로세스를 멀티스레드 프로세스(multi-threaded process)라고 한다<br/>

JVM 스택 영역<br/>

`프로그램 실행과정에서 임시로 할당되었다가 메소드를 빠져나가면 바로 소멸되는 특성의 데이터를 저장하기 위한 영역이다`<br/>

각종 형태의 변수나 임시 데이터, 스레드나 메소드의 정보를 저장한다<br/>

메소드 호출 시마다 각각의 스택 프레임(그 메서드만을 위한 공간)이 생성된다. 메서드 수행이 끝나면 프레임 별로 삭제를 한다 <br/>

메소드 안에서 사용되는 값들을 저장한다. 또 호출된 메소드의 매개변수, 지역변수, 리턴 값 및 연산시 일어나는 값들을 임시로 저장한다<br/>

### 1. Native method stack

`자바 프로그램이 컴파일되어 생성되는 바이트 코드가 아닌 실제 실행할 수 있는 기계어로 작성된 프로그램을 실행시키는 영역`

- JAVA가 아닌 다른 언어로 작성된 코드를 위한 공간
- Java Native Interface 를 통해 바이트 코드로 전환하여 저장하게 된다
- 일반 프로그램처럼 커널이 스택을 잡아 독자적으로 프로그램을 실행시키는 영역

### 2. Method Area (=Class Area = Static area)

`클래스 정보를 처음 메모리 공간에 올릴 때 초기화되는 대상을 저장하기 위한 메모리 공간`

### 3. Runtime Constant Pool

- 스태틱 영역에 존재하는 별도의 관리영역
- `상수 자료형을 저장하여 참조하고 중복을 막는 역할을 수행한다`

스태틱 영역에 저장되는 데이터<br/>

#### Field Information (멤버 변수)

- 멤버변수의 이름, 데이터 타입, 접근 제어자에 대한 정보

#### Method Information (메소드)

- 메소드의 이름, 리턴타입, 매개변수, 접근 제어자에 대한 정보

#### Type Information (타입)

- class인지 interface 인지의 여부 저장. Type의 속성, 전체 이름, super 클래스의 전체 이름.(interface 이거나 object 인 경우 제외된다. 이건 Heap 에서 관리함)

### Heap 영역

![Heap 영역](/assets/images/heap.png)

객체를 저장하는 가상메모리 공간. new 연산자로 생성되는 객체와 배열을 저장한다 <br/>

Class Area(Static Area)에 올라온 클래스들만 객체로 생성할 수 있다 <br/>

힙은 세 부분으로 나뉘어 진다<br/>

### Permanent Generation

직역하면 영구적인 세대이다 <br/>

생성된 객체들의 정보의 주소값이 저장된 공간이다. 클래스 로더에 의해 load 되는 Class, Method 등에 대한 Meta 정보가 저장되는 영역이고 JVM 에 의해 사용된다 <br/>

Reflection 을 사용하여 동적으로 클래스가 로딩되는 경우에 사용된다<br/>

### Reflection 이란?

- 객체를 통해 클래스의 정보를 분석해 내는 프로그래밍 기법
- 구체적인 클래스 타입을 알지 못해도, 컴파일된 바이트 코드를 통해 역으로 클래스의 정보를 알아내어 사용할 수 있다는 뜻이다<br/>

### New/Young 영역

이곳의 인스턴스들은 추후 가비지 콜렉터에 의해 사라진다 <br/>

생명 주기가 짧은 "젋은 객체"를 GC 대상으로 하는 영역이다 <br/>

여기서 일어나는 가비지 콜렉트를 Minor GC 라고 한다<br/>

### Eden

객체들이 최초로 생성되는 공간<br/>

### Survivor 0, 1 : Eden 에서 참조되는 객체들이 저장되는 공간


> Eden 영역에 객체가 가득차게 되면 첫번째 가비지 콜렉트가 발생한다<br/>

> Eden 영역에 있는 값 등을 Survivor 1 영역에 복사하고 이 영역을 제외한 나머지 객체를 삭제한다<br/>

### Old 영역

이곳의 인스턴스들은 추후 가비지 콜렉터에 의해 사라진다 <br/>

생명 주기가 긴 "오래된객체"를 GC 대상으로 하는 영역이다 <br/>

여기서 일어나는 가비지 콜렉트를 Major GC 라고 한다. Minor GC 에 비해 속도가 느리다 <br/>

New/Young Area 에서 일정시간 참조되고 살아 있는, 살아남은 객체들이 저장되는 공간이다<br/>

---

# JDK와 JRE의 차이

JDK

Java Development Kit (자바 개방 키트)<br/>

Java 를 사용하기 위해 필요한 모든 기능을 갖춘 Java 용 SDK (Software Development Kit)이다 <br/>

`Jdk 는 JRE 를 포함하고 있다`<br/>

JRE 에 있는 모든 것 뿐만 아니라 '컴파일러 (javac)와 jdb, javadoc' 과 같은 도구도 있다<br/>


즉, JDK 는 프로그램을 생성, 실행, 컴파일 할 수 있다<br/>


### JRE

Java Runtime Environment(자바 런타임 환경)<br/>

`JVM + 자바 클래스 라이브러리(Java Class Library) 등으로 구성되어 있다`<br/>

컴파일 된 Java 프로그램을 실행하는데 필요한 패키지이다<br/>


> 요약.

> JDK 는 자바 프로그램을 실행, 컴파일, 개발용 도구

> JRE, JVM 모두 포함하는 포괄적 키트이다

> JRE 는 자바 프로그램을 실행할 수 있게 하는 도구이다. JVM 을 포함하고 있다



### SDK 란?

- Software Development Kit (소프트웨어 개발 키드)
- 하드웨어 플랫폼, 운영체제 또는 프로그래밍 언어 제작사가 제공하는 툴이다. 키트의 요소는 제작사마다 다르다
- SDK 의 대표적인 예로, JDK 등이 있다
- SDK 를 활용하여 애플리케이션을 개발할 수 있다
