---
title:  "[Java] 추상 클래스와 인터페이스 " 
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

다음과 같이  

![그림 7-1](/assets/images/ex7-1.png)

