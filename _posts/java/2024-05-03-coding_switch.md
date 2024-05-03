---
title: "[Java] 4주차. 제어문"
categories: Java
tags:
  - Java
  - Programming
  - coding
toc: true
toc_sticky: true
date: 2024-05-03
last_modified_at: 2024-05-03
---

![java.png](/assets/images/java.png)

# **제어문**

## 1. 선택문 `swithc`

```
💡  조건에 따라 다른 문장이 수행되도록 하는 것
```

선택문은 조건식과 문장을 포함하는 블럭(`{}`) 으로 구성되어 있으며, 조건식의 연산결과에 따라 실행할 문장이 달라져서 프로그램의 흐름을 변경할 수 있다

조건문인 if문은 조건식의 결과가 참과 거짓 두 가지뿐이기에 경우의 수가 많아질수록 else-if 가 추가되야해서 복잡해질 수 있고 여러 조건식을 처리해야 해서 처리시간도 더 길다

`switch` 문은 하나의 조건식으로 여러 경우의 수를 처리할 수 있기에 처리할 경우의 수가 많을수록 if문보다는 `switch` 문을 사용하는게 좋다

```java
switch (조건식) {
	case 값1:
		//조건식의 결과가 값1과 같을 경우 수행될 코드
		break;
	case 값2 :
		//조건식의 결과가 값2와 같은 경우 수행될 코드
		break;
	default:
		//조건식의 결과와 일치하는 case문이 없을 경우 수행될 코드	
}
```

코드에서 조건식의 결과와 일치하는 값이 있는 `case`가 있는지 찾아서 찾는다면 해당 케이스의 코드를 수행하고, 만일 적절한 값을 찾지 못한다면 `default`의 코드를 수행한다. 여기서 각각의 케이스는 코드 수행 후 `break`문을 만나 전체 `switch`문을 빠져나가야하는데, 만일 `break`문이 없으면 종료되지않고 계속 진행이 된다. 그리고 `default`는 보통 마지막에 놓기 때문에 `break`문을 생략하는 경우도 있다

- break문을 작성한 코드

```java
public static void main(String[] args){ 
	int level = 3; 
	
	switch (level) { 
		case 3: 
			System.out.println("레벨이 3입니다."); 
			break; 
		case 2: 
			System.out.println("레벨이 2입니다."); 
			break; 
		case 1: 
			System.out.println("레벨이 1입니다."); 
			break; 
		default: 
			System.out.println("레벨을 측정할 수 없습니다."); 
	} 
}
```

- 실행결과

```
레벨이 3입니다.
```

break문을 작성한경우 level에 해당하는 케이스를 찾아 내용을 수행한 뒤 break문을 만나 switch문을 벗어난다. 그렇기에 `레벨이 3입니다.` 문구만 출력이되고 종료가 된다. 여기서 break문을 제거할경우 나머지 하위 조건들과 구분이 사라지기에 모든 코드가 실행되는것을 확인할 수 있다.

- break문을 작성하지 않은 코드

```java
public static void main(String[] args){ 
	int level = 2; 
	
	switch (level) { 
		case 3: 
			System.out.println("레벨이 3입니다."); 
		case 2: 
			System.out.println("레벨이 2입니다."); 
		case 1: 
			System.out.println("레벨이 1입니다."); 
		default: 
			System.out.println("레벨을 측정할 수 없습니다."); 
	} 
}
```

- 실행결과

```
레벨이 2입니다.
레벨이 1입니다.
레벨을 측정할 수 없습니다.
```

보는것과 같이 level은 2이기에 `레벨이 2입니다.` 만 축력되고 끝나야 하지만 case 2의 코드를 실행 후 break 문이 없기 때문에 그 하위 case를 모두 수행하고 switch문의 끝에 다다러서야 switch 문을 종료하고 벗어나게 된다. 그렇기에 레벨이 2임에도 불구하고 레벨이 1인경우와 측정불가인 기본 케이스가 모두 수행되는 문제가 생긴다

하지만, 고의적으로 break문을 생략하는 경우도 있다. 가령 예를들어 레벨에 따른 권한과 같이 레벨이 올라갈수록 하위요소를 다 포함하는 경우 break문이 없을 경우 하위 요소를 모두 실행해 포함시킬 수 있다

- break문이 없는 switch 응용

```java
public static void main(String[] args){ 
	int level = 2; 
	
	switch (level) { 
		case 3: 
			grantDelete(); // 삭제 권한을 부여한다. 
		case 2: 
			grandWrite(); // 쓰기 권한을 부여한다. 
		case 1: 
			grandRead(); // 읽기 권한을 부여한다. 
	} 
}
```

위와 같이 사용한다면 레벨에 따라 3인사람은 `읽기`/`쓰기`/`삭제` 권한을 모두 가질 수 있고, 레벨 2는 `쓰기`/`읽기`, 레벨 1은 `읽기` 권한만 가지도록 할 수 있다

다음으로는 switch문의 제약조건에 대해 알아보자


### **switch문의 제약조건**

- switch문의 조건식 결과는 정수 또는 문자열이어야 한다
- case문의 값은 정수 상수만 가능하며, 중복되지 않아야 한다

```java
final int ONE = 1; 

switch(condition){ 
	case '1': //OK. 문자 상수(정수 상수 49와 동일) 사용 가능 
	case ONE: //OK. 정수 상수 사용 가능 
	case "YES": //OK. 문자열 상수 사용 가능 
	case num; //에러. 변수는 불가 
	case 1.0: //에러. 실수는 불가 
}
```

### **OR조건식의 간결화**

1년 12개월의 봄/ 여름/ 가을/ 겨울을 조건문(else-if)문을 통해 구현하려고 하면 상당히 복잡하다

```java
if (month == 3 || month == 4 || month == 5) { 
	System.out.println("봄"); 
} else if (month == 6 || month == 7 || month == 8) { 
	System.out.println("여름"); 
} else if (month == 9 || month == 10 || month == 11) { 
	System.out.println("가을"); 
} else { // month == 12 || month == 1 || month == 2 
	System.out.println("겨울"); 
}
```

수만은 else-if 조건식과 or연산을 해줘야 한다. 이런 경우 switch를 쓰면 한결 간결한 표현이 가능하다

```java
switch (month) { 
	case 3: case 4: case 5: 
		System.out.println("봄"); 
		break; 
	case 6: case 7: case 8: 
		System.out.println("여름"); 
		break; 
	case 9: case 10: case 11: 
		System.out.println("가을"); 
		break; 
	default: //case 12: case 1: case 2 
		System.out.println("겨울"); 
}
```

### **switch문의 중첩사용**

switch문 역시 중첩사용이 가능하다. 사용방법은 else-if와 같이 case안에 swith문을 작성해주면 된다

```java
  
public static void main(String[] args){ 
	int month = 3; 
	int time = 13; 
	
	switch (month) { 
		case 3: case 4: case 5: 
			System.out.println("봄"); 
			switch (time) { 
				case 1: case 2: case 3: case 4: 
					System.out.println("새벽"); 
					break; 
				case 5: case 6: case 7: case 8: 
					System.out.println("아침"); 
					break; 
				case 9: case 10: case 11: case 12: 
					System.out.println("오전"); 
					break; 
				case 13: case 14: case 15: case 16: case 17: case 18:
					System.out.println("오후"); 
					break; 
				default: 
					System.out.println("저녁"); 
					break; 
			} 
			break; 
		case 6: case 7: case 8: 
			System.out.println("여름"); 
			break; 
		case 9: case 10: case 11: 
			System.out.println("가을"); 
			break; 
		default: //case 12: case 1: case 2 
			System.out.println("겨울"); 
	} 
}
```

---

## 2. 반복문 `for`,`while`,`do-while`

```
💡 특정 문장들을 반복해서 수행하는 것
```

반복문은 특정 작업을 반복수행하기 위해 사용된다. 반복문의 종류로는

- `for`
- `while`
- `do-while`

이렇게 있으며 위 두 반복문은 조건에 따라 한 번도 수행되지 않을 수 있지만, `do-while`은 조건식의 연산결과 평가는 우선 `do`를 통해 수행한 뒤에 하기 때문에 일단 1회 수행된다는 차이점이 있다

### **for문**

- 특징
	- 반복 횟수를 알고 있을 때 적합
	- 구조는 복잡하지만, 직관적이다

- 구조

![for문](https://oopy.lazyrockets.com/api/v2/notion/image?src=https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fb313bc58-5126-4e59-bc35-444943a5d677%2FUntitled.png&blockId=93e23c48-4b53-47cc-b41c-7b02daa6c89c)

1. **초기화 1)** : for 문의 기준이 될 변수의 초기값 설정으로 위 구조에서는 `int` 타입의 `i` 에 `1` 을 설정해줬다
2. **조건식 2)** : for문이 수행될 조건으로 해당 조건이 `true`가 되는동안 반복이 수행된다
3. **증감식 3)** : 코드수행 후 조건평가 전 수행되며, 위 구조에서는 `i`를 1씩 후위 증가해주고 있다

- for문의 수행순서

![for문의 수행순서](https://oopy.lazyrockets.com/api/v2/notion/image?src=https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F5e93f5c1-275a-4355-a917-c72b491e0fbe%2FUntitled.png&blockId=95bedcee-a18b-470a-a272-5ff808374681)

- **for문의 예제코드**

	구구단을 for 문으로 작성해본다

```java
public static void main(String[] args) { 
	for (int i = 2; i <= 9; i++) { 
		for (int j = 1; j <= 9; j++) { 
			System.out.printf("%d x %d : %d%n", i, j, i * j); 
		} 
	} 
}
```

- **향상된 for문(enhanced for statement)**

JDK1.5 부터 배열과 컬렉션에 저장된 요소에 접근할 때 기존보다 편리한 방법으로 접근할 수 있도록 for 문의 새로운 문법이 추가되었다

```
➡️ for(타입 변수명 : 배열 또는 컬렉션) {
	//반복할 문장
}
```

이 for문을 사용하기 위해서는 타겟이될 인수가 배열 또는 컬렉션의 요소의 타입이어야 한다. 타겟 요소를 매 반복마다 하나씩 순서대로 읽어서 변수에 저장 후 블럭 (`{}`)내에서 수행한다

```java
public static void main(String[] args) { 
	String[] strings = new String[]{"catsbi", "pobi", "crong", "whiteship", "tobi"}; 
	
	for (String string : strings) { 
		System.out.println("current string:" + string); 
	} 
}
```

- 실행결과

```
current string:catsbi
current string:pobi
current string:crong
current string:whiteship
current string:tobi
```

### **while문**

```
➡️ while(조건식) {
	//조건식의 연산결과가 참(true)인 동안 실행될 코드
}
```

if문과 같이 조건식과 블럭만으로 이루어져있어서 간결하다. 다만, if문과는 다르게 while문은 조건식이 참(true)인 동안 블럭내의 문장을 반복한다

- **구조**

![while문](https://oopy.lazyrockets.com/api/v2/notion/image?src=https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F786383cd-f868-47ce-bcfa-d33a50df3fd7%2FUntitled.png&blockId=590175a9-4c06-42e3-84f1-5d08a60368d1)


1. 조건식이 참일경우 블럭안으로 들어가고 거짓일경우 while문을 벗어난다
2. 블럭`{}`의 문장을 수행하고 다시 조건식으로 돌아간다

- **예제 코드**

for 문에서 구현한 구구단을 while 문으로 구현해본다

```java
public static void main(String[] args) { 
	int i = 2, j = 1; 
	
	while (i <= 9) { 
		while (j <= 9) { 
			System.out.printf("%d x %d : %d%n", i, j, i * j); 
			j++; 
		} 
		i++; 
		j = 1; 
	} 
}
```

실행결과는 for문으로 구현한 구구단과 동일하다

- **for문과 while 문의 비교**
     - for 문은 초기화, 조건식, 증감식을 한 곳에 모아놓았다는 것을 제외하면 while문과 다를바 없다. 그렇기에 서로 변환이 가능하다. 상황에 따라 초기화나 증감식이 필요하지 않은 경우 while 문을 사용하고 그렇지 않으면 for문을 쓰면 된다

 -  while 문의 조건식은 생략불가
	- 한 가지 주의할 점은 for문과 달리 while 문의 조건식은 생략할 수 없다

```java
while(){ //에러 발생. 조건식이 없음
	//수행될 코드
}

for(;;){ //조건식이 항상 참(true)
	//수행될 코드
}
```

그렇기에 while문의 조건식이 항상 참이 되도록 하려면 반드시 true를 넣어야한다

### **do-while문**

while문의 변형인 do-while문은 기본적인 구조는 while문과 동일하지만 조건식과 블럭의 순서를 바꿔놓은 것으로, 기존의 while문과는 반대로 블럭을 먼저 수행 후 조건식을 평가한다

그렇기에 다른 반복문과는 다르게 최소 한 번은 수행될 것을 보장한다

```java
do{
	//수행될 로직
} while (조건식);
```

- **예제코드**

UpAndDown 게임을 만들어 본다

```java
public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int input = 0, answer = 0;
    answer = new Random().nextInt(10);

    do{
        System.out.println("1~10사이의 숫자를 입력해주세요.");
        input = Integer.parseInt(sc.nextLine());

        if (input > answer) {
            System.out.println("Down");
        } else if(input < answer) {
            System.out.println("Up");
        }

    }while (answer != input);
}
```

1~10사이의 정수값을 answer에 저장한 이후 사용자에게 값을 입력받아 UpAndDown을 하는 게임인데, 이처럼 최초에 1회 입력을 받아 비교해야하는 경우에는 do-while 이 적합하다

- **break문**

선택문 부분에서 사용했던 break문을 반복문에서도 사용할 수 있다

switch문과 같이 break문은 자신이 포함된 가장 가까운 반복문을 벗어난다. 그렇기에 보통 조건문(`if`)과 같이 사용되어 특정 조건을 만족하면 반복문을 벗어나도록 할 때 사용한다

- **예제 코드**

변수 `sum`의 값이 100이되면 멈추는 반복문을 구현한다

```java
public static void main(String[] args) {
	int sum = 0, count = 0;

    while (true) {
        if (sum >= 100) {
            break;
        }
				count++;
        sum  += count;
    }

		System.out.printf("count:%d, sum:%d",count, sum);
}
```

반복문의 조건식은 `true`로 무한순회하며 sum에 후위증감하는 count를 계속해서 더해나간다

- **continue문**

`continue`문은 반복문 내에서만 사용되며, 반복이 진행되는 도중에 `continue`문을 만나면 반복문의 끝으로 이동하여 다음 반복으로 넘어간다. 즉 반복문을 벗어나기보단 해당 반복문을 패스한다고 보면 된다. for 문의 경우 증감식으로 이동하며 `while`문과 `do-while`문은 조건식으로 이동한다

반복문을 벗어나지 않고 다음 반복을 수행할 수 있기에 주로 `if`문과 함께 사용되어 특정 조건을 만족할 경우 `continue`문이 다음 코드를 수행하지 않고 다음 반복으로 넘어가서 진행하도록 한다

- **예제코드**

짝수만 출력하는 반복문(for)을 구현한다

```java
public static void main(String[] args) {
    for (int i = 1; i < 50; i++) {
        if (isOdd(i)) {
            continue;
        }
        System.out.println("value: " + i);
    }
}

private static boolean isOdd(int i) {
    return i % 2 == 1;
}
```

`i`가 홀수인 경우 `continue`를 통해 해당 출력 코드를 패스하고 다음 반복을 수행한다

- **이름 붙은 반복문**

break문은 근접한 하나의 반복문만 벗어날 수 있기에, 여러 반복문이 중첩된 경우 break문으로 중첩 반복문을 완전히 벗어날 수 없다. 이때는 중첩 반복문 앞에 이름을 붙혀 break문과 continue문에 이름을 지정해 하나 이상의 반복문을 벗어나거나 건너뛸 수 있다

- 예제 코드 - continue 사용

```java
public static void main(String[] args) {
    Loop1:
    for (int i = 2; i <= 9; i++) {
        for (int j = 1; j <= 9; j++) {
            if (i + j > 5)
                continue Loop1;

            System.out.printf("%d x %d : %d%n", i, j, i * j);
        }
        System.out.println();
    }
}
```

`i + j`가 `5`보다 크면 `Loop1`의 반복문을 `continue` 하여 다음 구구단 (2단->3단->4단...)을 수행하도록 했다

- 예제코드 -break 사용

```java
public static void main(String[] args) {
    Loop1:
    for (int i = 2; i <= 9; i++) {
        for (int j = 1; j <= 9; j++) {
            if (j == 5)
                break Loop1;
            System.out.printf("%d x %d : %d%n", i, j, i * j);
        }
        System.out.println();
    }
}
```

`j`가 `5`가 되면 `Loop1` 반복문을 종료시켜 2단의 4번째인 `2 x 4` 연산까지만 수행하고 `2 x 5` 가 될 때 반복문은 종료된다

---


