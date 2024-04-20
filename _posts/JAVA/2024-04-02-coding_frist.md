---
title:  "[Java] 문장 출력하기" 

categories:
  -  Java
tags:
  - [Java, Programming, coding]

toc: true
toc_sticky: true

date: 2024-04-02
last_modified_at: 2024-04-02
---

![java.png](..%2Fassets%2Fimg%2Fjava.png)

# Java 첫 기초연습

>"hello,java" 라는 문장을 화면에 출력하세요

~~~java
package hello;
// "hello,java"라는 문장을 화면에 출력하세요  <--주석처리(출력에는 영향을 미치치 않는다
public class hellojava {
    public static void main(String[] args) {
        System.out.println("hello, java");
    }
}
~~~

- 출력값

~~~
hello, java

Process finished with exit code 0
~~~

오 신기한데 아직은 이게 뭔가 싶다 ㅎㅎ 


1. System.out.println()이라는 명령어는 출력을 해준다.
2. 문자열은 " "쌍따옴표로 감싸준다.
3. 선언이 끝난뒤에는 ; 세미콜론을 사용하고, 제어문, 클래스, 메소드 등이 끝나면 {} 대괄호를 사용한다. 
4. public class <<-- 에서 알수 있다 싶이 class 다음에 오는 hellojava가 class 이름이다.

> 한 줄 주석과 여러줄 주석 표시하기

~~~java
package hello;

public classs HelloJava {
    public static void main(String[] args){
        //System.out.println("Hello, Java");  <--한줄 주석 연습
    }
}
~~~

> 인텔리제이 단축키 (ctrl + /)


- 문장앞에 //표시를 하면 주석으로 처리되고 컴파일이 되지 않는다.
- 한줄 주석은 간단한 코멘트를 작성하거나 코드 바로 앞에 설명하는데 주로 쓰인다.

~~~java
/*
 DATE : 2018년 5월 8일
 Author : 박은종
 Descripion : 첫 번째 자바 프로그램입니다.
 Version : 1.0
*/
package hello;

public class HelloJava {
    public static void main(String[]args) {
        System.out.println("Hello, Java");
    }
}
~~~

> 인텔리제이 단축기 (ctrl + shift + /)


- 여러줄 주석 표시하기
- 여러줄 주석 처리는 /* . */기호의 시작과 끝을 나타낼 수 있다. 여러줄 주석은 코드의 여러줄을 한꺼번에 주석처리 하거나 코드에 대해 길게 설명할때 사용한다

