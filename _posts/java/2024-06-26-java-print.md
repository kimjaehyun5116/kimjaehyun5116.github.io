---
title:  "[Java] 자바 기본 입출력" 
categories: Java
tags: [Java, Programming, coding]
toc: true
toc_sticky: true
date:  2024-06-26
last_modified_at:  2024-06-26
---

![java.png](/assets/images/java.png)

# 자바 기본 입출력

여태까지 프로그램을 작성할 때 `System.out.println()`을 계속 사용해 실행결과를 확인해 왔는데, 
이는 자바에서 데이터를 출력할 수 있도록 매표 메서드로 `System.out` 이라는 객체를 사용하기 때문이다.
반대로 키보드로 데이터를 입력받을 때는 `System.in` 객체를 사용한다

![데이터의 입출력](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fb2Qk9E%2FbtqEPlqp9QI%2F4kQjpdiztcNCjGO7YbnrU1%2Fimg.png)

## 화면에 데이터 출력

자바에서는 콘솔 뷰로 데이터를 출력하려고 다음 메서드들을 제공하는데, 모두 `System.out` 객체와 연결해 사용한다

- `println()` : () 내부의 내용을 출력한 후 행을 바꾼다
- `print()` : () 내부의 내용을 출력만 하고 행은 바꾸지 않는다
- `printf()` : () 내부의 내용을 지정된 포맷을 사용해 출력한다

포맷을 지정해서 출력하는 printf() 메서드는 %로 시작하는 포맷을 여러 개 포함할 수 있는 포맷 명시자를 사용한다. 단, 이 포맷 개수와 포맷을 적용할 데이터 개수는 서로 같아야 한다

```java
System.out.printf("포맷 명시자", 데이터, 데이터, ∙∙∙);
```

(a) 사용 형식

```java
int x = 5;      // x 변수를 10진수 정수 포맷과 대응시킨다.
double pi = 3.14;       // pi 변수를 10진수 실수 포맷과 대응시킨다

System.out.print("x = %d and pi = %f\n", x, pi);
```
printf() 메서드는 기본적으로 오른쪽으로 정렬해서 출력하지만 % 다음에 마이너스 표시(-)가 있으면 왼쪽으로 정렬해서 출력한다.
% 다음에 숫자가 있다면 출력될 자릿수를 지정한다. 실수는 %a,b로 표현할 수 있는데, 여기서 a는 소수점 이하의 숫자까지 포함해 출력될 최소
자릿수를 나타내고, b는 소수점 이하 자릿수를 나타낸다. 출력할 내용이 자릿수보다 작다면 기본적으로 공백으로 채우지만, % 다음에 0이 있다면 0으로 채운다.
탭`Tab`, 줄 바꿈,`%` 기호를 출력하려면 각각 `\t`,`\n`,`%%`로 표현한다

---

| 종류  |  데이터   |   포맷   |     실행결과     |           설명            |
|:---:|:------:|:------:|:------------:|:-----------------------:|
| 정수  |   97   |   %d   |      97      |          10진수           |
|     |        |   %o   |     141      |           8진수           |
|     |        |   %x   |      61      |          16진수           |
|     |        |   %c   |      a       |           문자            |
|     |        |  %5d   |      97      |    5자리. 빈자리는 공백처리한다     |
|     |        |  %-5d  |      97      | 5자리. 빈자리는 공백 처리한다. 왼쪽정렬 |
|     |        |  %05d  |    00097     |    5자리. 빈자리는 0으로 채운다    |
| 문자열 | "java" |   %s   |    "java"    |           문자열           |
|     |        |  %5s   |   " java"    |    5자리. 빈자리는 공백 처리한다    |
|     |        |  %-5s  |    "java"    | 5자리. 빈자리는 공백 처리한다. 왼쪽정렬 |
| 실수  | 3.14f  |   %f   |   3.140000   |         10진수 실수         |
|     |        |   %e   | 3.140000e+00 |           지수            |
|     |        | %4.1f  |     3.1      |     4자리. 소수점 이하 1자리     |
|     |        | %04.1f |     03.1     |  4자리. 소수점 이하 1자리. 빈자리   |
|     |        | %-4.1f |     3.1      |  4자리. 소수점이하 1자리. 왼쪽정렬   |

---

포맷을 이용한 화면 출력

```java
public class PrintfDemo {
  public static void main(String[] args) {
    int i = 97;
    String s = "java";
    double f = 3.14f;
    System.out.printf("%d\n", i);
    System.out.printf("%o\n", i);
    System.out.printf("%x\n", i);
    System.out.printf("%c\n", i);
    System.out.printf("%5d\n", i);
    System.out.printf("%05d\n", i);
    System.out.printf("%s\n", s);
    System.out.printf("%5s\n", s);
    System.out.printf("%-5s\n", s);
    System.out.printf("%f\n", f);
    System.out.printf("%e\n", f);
    System.out.printf("%4.1f\n", f);
    System.out.printf("%04.1f\n", f);
    System.out.printf("%-4.1f\n", f);
  }
}
```

출력값

```
97
141
61
a
   97
00097
Java
 Java
Java
3.140000
3.140000e+00
 3.1
03.1
3.1
```

---

## 키보드로 데이터 입력
