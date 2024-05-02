---
title:  "[Java] super 키워드" 
categories: Java
tags: [Java, Programming, coding]
toc: true
toc_sticky: true
date:  2024-06-16
last_modified_at:  2024-06-16
---

![java.png](/assets/images/java.png)

> ### super 와 super() 

`super`

- 자식클래스를 이용해서 객체를 생성할 때 부모 생성자를 호출해서 부모 클래스의 인스턴스도 같이 생성하게 된다
- 이 때 생성한 부모의 인스턴스 주소를 보관하는 래퍼런스 변수로 자식 클래스 내의 모든 생성자와 메소드 내에서 선언하지 않고도 사용할 수 있는 래퍼런스 변수이다

`super()`

- 부모 생성자를 호출하는 구문으로 인자와 매개변수 타입, 갯수, 순서가 일치하는 부모생정자를 호출하게 된다
- this() 가 해당 클래스 내에 다른 생성자를 호출하는 구문이라면 super() 는 부모클래스가 가지는 private 생성자를 제외한 나머지 생성자를 호출할 수 있도록 하는 구문이다

---

super_keyword 를 사용한 예제

```java
package section02.superkeyword;

import java.util.Date;

public class Computer extends Product{
    private String cpu;
    private int hdd;
    private int ram;
    private String operationSystem;

    public Computer(){
        System.out.println("Computer 클래스의 기본생성자 호출함...");
    }

    public Computer(String cpu, int hdd, int ram, String operationSystem) {
        super();
        this.cpu = cpu;
        this.hdd = hdd;
        this.ram = ram;
        this.operationSystem = operationSystem;

        System.out.println("Computer 클래스의 모든 필드를 초기화하는 생성자 호출함...");
    }

    public Computer(String code, String brand, String name, int price, Date manufacturingDate, String cpu, int hdd, int ram, String operationSystem) {
        super(code, brand, name, price, manufacturingDate);
        this.cpu = cpu;
        this.hdd = hdd;
        this.ram = ram;
        this.operationSystem = operationSystem;

        System.out.println("Computer 클래스의 부모 필드도 초기화하는 생성자 호출함///");
    }

    public String getCpu() {
        return cpu;
    }

    public void setCpu(String cpu) {
        this.cpu = cpu;
    }

    public int getHdd() {
        return hdd;
    }

    public void setHdd(int hdd) {
        this.hdd = hdd;
    }

    public int getRam() {
        return ram;
    }

    public void setRam(int ram) {
        this.ram = ram;
    }

    public String getOperationSystem() {
        return operationSystem;
    }

    public void setOperationSystem(String operationSystem) {
        this.operationSystem = operationSystem;
    }

    @Override
    public String getInformation() {
        return super.getInformation()
                + "Computer cpu = " + this.cpu +
                ", hdd " + this.hdd + ", ram = " +this.ram +
                "operationSystem = " + this.operationSystem;
    }
}
```
```java
package section02.superkeyword;

import java.util.Date;

public class Product {

    private String code; //상품코드
    private String brand; //제조사명
    private String name; //상품명
    private int price;   //가격
    private Date manufacturingDate;  //제조일자

    public Product(){
        System.out.println("Product 클래스의 기본 생성자 호출함... ");
    }

    public Product(String code, String brand, String name, int price, Date manufacturingDate) {
        this.code = code;
        this.brand = brand;
        this.name = name;
        this.price = price;
        this.manufacturingDate = manufacturingDate;
        System.out.println("Product 클래스의 매개변수 있는 생성자 호출함... ");
    }

    public String getCode() {
        return code;
    }

    public void setCode(String code) {
        this.code = code;
    }

    public String getBrand() {
        return brand;
    }

    public void setBrand(String brand) {
        this.brand = brand;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getPrice() {
        return price;
    }

    public void setPrice(int price) {
        this.price = price;
    }

    public Date getManufacturingDate() {
        return manufacturingDate;
    }

    public void setManufacturingDate(Date manufacturingDate) {
        this.manufacturingDate = manufacturingDate;
    }


    public String getInformation() {
        return "Product{" +
                "code='" + code + '\'' +
                ", brand='" + brand + '\'' +
                ", name='" + name + '\'' +
                ", price=" + price +
                ", manufacturingDate=" + manufacturingDate +
                '}';
    }
}
```
```java
package section02.superkeyword;

import java.util.Date;

public class Application {
    public static void main(String[] args) {
        
        Product product1 = new Product();
        System.out.println("product1.getInformation() = " + product1.getInformation());

        Product product2 = new Product("S-01234", "삼성", "갤럭시Z폴드5", 3590000, new java.util.Date());
        System.out.println("product2.getInformation() = " + product2.getInformation());

        Computer computer1 = new Computer();
        System.out.println("computer1.getInformation() = " + computer1.getInformation());

        Computer computer2 = new Computer("퀼컴 스냅드래곤", 512, 12, "안드로이드");
        System.out.println("computer2.getInformation() = " + computer2.getInformation());

        Computer computer3 = new Computer("S-01234", "삼성", "갤럭시Z폴드5", 2590000, new java.util.Date(),
                "퀼컴 스냅드래곤", 512, 12, "안드로이드");
        System.out.println("computer3.getInformation() = " + computer3.getInformation());
    }

}
```

---

출력 값

```
Product 클래스의 기본 생성자 호출함... 
product1.getInformation() = Product{code='null', brand='null', name='null', price=0, manufacturingDate=null}
Product 클래스의 매개변수 있는 생성자 호출함... 
product2.getInformation() = Product{code='S-01234', brand='삼성', name='갤럭시Z폴드5', price=3590000, manufacturingDate=Thu Apr 25 21:20:03 KST 2024}
Product 클래스의 기본 생성자 호출함... 
Computer 클래스의 기본생성자 호출함...
computer1.getInformation() = Product{code='null', brand='null', name='null', price=0, manufacturingDate=null}Computer cpu = null, hdd 0, ram = 0operationSystem = null
Product 클래스의 기본 생성자 호출함... 
Computer 클래스의 모든 필드를 초기화하는 생성자 호출함...
computer2.getInformation() = Product{code='null', brand='null', name='null', price=0, manufacturingDate=null}Computer cpu = 퀼컴 스냅드래곤, hdd 512, ram = 12operationSystem = 안드로이드
Product 클래스의 매개변수 있는 생성자 호출함... 
Computer 클래스의 부모 필드도 초기화하는 생성자 호출함///
computer3.getInformation() = Product{code='S-01234', brand='삼성', name='갤럭시Z폴드5', price=2590000, manufacturingDate=Thu Apr 25 21:20:04 KST 2024}Computer cpu = 퀼컴 스냅드래곤, hdd 512, ram = 12operationSystem = 안드로이드
```

`코드리뷰`

제품(Product)과 컴퓨터(Computer) 클래스를 포함하고 있는 패키지에 제품 및 컴퓨터 객체를 생성하고 정보를 출력하는 예시이다

1. **클래스 구조** : Product 클래스는 제품의 기본 속성을 정의하고, Computer 클래스는 이 속성에 더하여 컴퓨터의 특징을 추가로 정의한다. Computer 클래스는 Product 클래스를 상속하여 확장된다
2. **생성자** : 각 클래스에는 기본 생성자와 매개변수를 받는 생성자가 정의되어 있다. 매개 변수를 받는 생성자는 각 필드를 초기화하고, 부모 클래스의 생성자를 호출해서 공통된 필드를 초기화한다
3. **super 키워드** : Computer 클래스에서 부모 클래스인 Product 클래스의 생성자를 호출할 때 `super()`키워드를 사용한다. 부모클래스의 생성자를 명시적으로 호출해서 부모 클래스의 필드를 초기화한다
4. **메소드 오버라이드** : Computer 클래스에서는 `getInformation()`메소드를 오버라이드해서 컴퓨터의 특징도 포함된 정보를 반환한다
5. **객체 생성 및 정보 출력** : Application 클래스에서 제품과 컴퓨터 객체를 생성하고, 각 객체의 정보를 출력한다. 생성된 제품 및 컴퓨터의 정보는 각 객체의 `getInformation()` 메소드를 통해 얻어온다

---

> 요약

- 이 코드는 클래스, 상속, 생성자, 메소드 오버라이드 등 자바의 기본적인 개념을 활용해서 객체지향 프로그래밍을 잘 보여준다
