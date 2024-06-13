---
title:  "[Java] 롬복(lombok) 에러 (java: java.lang.NoSuchFieldError: Class com.sun.tools.javac.tree.JCTree$JCImport does not have member field 'com.sun.tools.javac.tree.JCTree qualid')"
categories: Java
tags: [Java, Programming, Coding]
toc: true
toc_sticky: true
date: 2024-06-13
last_modified_at: 2024-06-13
---

![java.png](/assets/images/java.png)

> # 문제상황

프로젝트 코드 작성 중

~~~
java: java.lang.NoSuchFieldError: Class com.sun.tools.javac.tree.JCTree$JCImport does not have member field 'com.sun.tools.javac.tree.JCTree qualid'
~~~

라는 에러와 함께 빌드 실패

> # 해결

JDK21 이상 버전과 호환되지 않는 롬복(lombok) 버전의 문제로 확인, (JDK21과 호환되는 최소 롬복(lombok) 버전은 1.18.30 이다.)

~~~
<!-- https://mvnrepository.com/artifact/org.projectlombok/lombok -->
<dependency>
     <groupId>org.projectlombok</groupId>
          <artifactId>lombok</artifactId>
          <version>1.18.30</version>
          <scope>provided</scope>
</dependency>
~~~

또는

~~~
dependencies {
      compileOnly 'org.projectlombok:lombok:1.18.30'
      annotationProcessor 'org.projectlombok:lombok:1.18.30'
}
~~~

기존 사용 중인 구버전 롬복(lombok)을 JKD21 호환 최소 버전인 1.18.30으로 변경해 주면 정상적으로 빌드가 된다

> # 추가

java: java.lang.NoSuchFieldError: Class com.sun.tools.javac.tree.JCTree$JCImport does not have member field 'com.sun.tools.javac.tree.JCTree qualid

해당 에러는 롬복 뿐만 아니라 JDK21에서 호환 안 되는 라이브러리가 있을 시 자주 보이는 에러이다. 혹시 JDK 업데이트 중 해당 에러를 발견한 것이라면, 롬복뿐 아니라 다른 라이브러리에 대한 버전 검토를 해야 한다.

참고

[링크](https://stackoverflow.com/questions/77171270/compilation-error-after-upgrading-to-jdk-21-nosuchfielderror-jcimport-does-n)


maven repo : [링크](https://mvnrepository.com/artifact/org.projectlombok/lombok/1.18.30)
