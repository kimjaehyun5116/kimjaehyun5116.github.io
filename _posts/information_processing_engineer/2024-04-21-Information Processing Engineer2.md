---
title:  "정보처리기사(2과목 소프트웨어 개발)"
categories: IPE
tags: [정보처리기사, 정처기]
toc: true
toc_sticky: true
date: 2024-04-21
last_modified_at: 2024-04-23
---

![정보처리기사](https://search.pstatic.net/common/?src=http%3A%2F%2Fblogfiles.naver.net%2FMjAyMzA2MTlfMTY2%2FMDAxNjg3MTQ5NzAwNDAw.ypuz7O1nB3m1HXGrghB9f7oBNb8a9aEquqxxiqmg7C4g.BsgTEfuIhphydLReLfkm3hk8ByGzBsPV20sSMARDm6og.PNG.asd5647%2F%25BE%25DF2-20230619-134121.png&type=sc960_832)
---
<BR/>

# 2과목 소프트웨어 필기 (요약)

---

> ## 20. 애플리케이션 패키징

**패키징**

- 개발이 완료된 소프트웨어를 고객에 인도하기 위해 패키징하고, 설치 매뉴얼, 사용 매뉴얼 등을 자성하는 일련의 배포용 설치 파일을 만드는 작업을 의미한다
- 향후 관리 편의성을 위해 모듈화하여 패키징한다
- 사용자를 중심으로 진행하며, 사용자의 다양한 환경에서 설치 할 수 있도록 패키징한다
- 사용자의 불편함을 줄이고 사용자의 편의성을 먼저 고려한다
- **패키징 시 주의 사항** : 전체 내용을 포함, 고객 중심, 모듈화, 버전 관리 및 릴리즈 노트 관리

**패키징 도구 활용 시 고려 사항**
- 제품 SW 종류에 적합한 암호화 알고리즘을 적용한다
- 패키징 도구를 활용하여 여러 가지 이기종 콘텐츠 및 단말기간 DRM 연동을 고려한다

---
 
> ## 21. 형상 관리(Version Control Revision Control)

**형상 관리**

- 구성관리(Software Configuration Management)라고도 한다
- 소프트웨어에 가시성과 추적 가능성을 부여하여 제품의 품질과 안정성을 높인다
- 형상 관리를 위해 구성된 팀은 형상통제위원회이다
- 소프트웨어 개발 생명주기 전반에 걸쳐 생성되는 소스 코드와 문서 등과 같은 산출물의 종합 및 변경 과정을 체계적으로 관리하고 유지하는 일련의 개발 관리 활동이다
- 형상 식별, 형상 통제, 형상 상태 보고, 형상 감사를 통하여 변경사항을 관리한다
- 이전 리버전이나 버전에 대한 정보에 접근 간으하여 배포본관리에 유용하다
- 불필요한 사용자의 소스 수정을 제한 할 수 있다
- 동일한 프로젝트에 대해 여러 개발자 동시 개발이 가능하다

**대표적인 소프트웨어 형상 목록**

- 프로젝트 요구 분석서, 운영 및 설치 지침서, 요구사항 명세서, 설계 / 인터페이스 명세서, 테스트 설계서, 소프트웨어 품질보증, 형상 관리, V&V 계획서와 같은 계획서, 코드 모듈(소스와 오브젝트 모두)

---

> ## 22. SW 테스트

**인수 테스트**

- 일반적인 테스트 레벨의 가장 마지막 상위 레벨로, SW 제품에 대한 요구사항이 제대로 이행되었는지 확인하는 단계이다
- 테스팅 환경을 실사용자 환경에서 진행하며 수행하는 주체가 사용자이다
- 알파, 베타 테스트와 가장 밀접한 연관이 있다
  - **알파 테스트** : 베타 테스트 전에 프로그램 개발 시 내부에서 미리 평가하고 버그를 찾아 수정하기 위해 시험해보는 검사이다
  - **베타 테스트** : 정식으로 프로그램을 공개하기 전에 한정된 집단 또는 일반인에게 공개하여 기능을 시험하는 검사이다
 
**결함 집중(Defect Clustering)**

- 파레토 법칙이 좌우한다
- 애플리케이션 결함의 대부분은 소수의 특정한 모듈에 집중되어 존재한다
- 결함은 발생한 모듈에서 계속 추가로 발생할 가능성이 크다

---

> ## 23. 단위 테스트(Unit Test)

**단위 테스트 정의**

- 하나의 모듈을 기준으로 독립적으로 진행되는 가장 작은 단위의 테슨트이다
- 애플리케이션을 구성하는 하나의 기능이 올바르게 동작하는지를 독립적으로 테스트하는 것이다
- 구현 단계에서 각 모듈의 개발을 완료한 후 개발자가 명세서의 내용대로 정확히 구연되었는지 테스트한다
- 모듈 내부의 구조를 구체적으로 볼 수 있는 구조적 테스트를 주로 시행한다

**단위 테스트 지원 도구(xUnit)**

- **JUni** : Java 프로그래밍 언어에 사용되는 테스트 도구로서 데이터를 테스트한 다음 코드에 삽입한다
- **NUnit** : 모든 .net 언어에 널리 사용되는 단위 테스트 프레임워크로 병렬로 실행할 수 있는 데이터 중심 테스트를 지원한다
- **JMockit** : 오픈소스 단위 테스트 도구로 기록 및 검증 구문으로 API 를 Mocking 할 수 있다
- **EMMA** : 코드 분석 오픈소스 툴킷으로 Java 기반이므로 외부 라이브러리 종속성이 없으며 소스 코드에 액세스 할 수 있다
- **PHPUnit** : PHP 프로그래머를 위한 단위 테스트 도구이다
- **HttpUnit** : Java 프로그램용 GUI가 없는 브라우저를 포함하는 오픈소스 Java 라이브러리이다
- **DBUnit** : 데이터베이스 단위 테스트를 지원하는 프레임워크이다

---

> ## 24. 테스트 스텁(Stub)과 테스트 트라이버(Driver)

Test Stub
- 상위 모듈에서 하위 모듈 방향으로 통합 테스트를 진행하는 하향식 테스트에서 사용한다
- 상위 모듈에서 하위 모듈로의 테스트를 진행하는 과정 중 하위 시스템 컴포넌트의 개발이 완료되지 않은 상황에서 시스템 테스트를 진행하기 위하여 임시로 생성된 가상의 더미 컴포넌트(Dummy Component)를 일컫는다

Test Driver
- 하위 모듈에서 상위 모듈로 통합하면서 테스트하는 상향식 테스트에서 사용한다
- 테스트할 소프트웨어 또는 시스템을 제어하고 동작시키는데 사용되는 도구를 의미한다
- 시스템이나 시스템 컴포넌트를 시험하는 환경 일부분으로 시험을 지원하는 목적하에 생성된 코드와 데이터이다

---

> ## 25. 통합테스트

통합테스트

- 단위 테스트를 통과한 개발 소프트웨어 / 하드웨어 컴포넌트간 인터페이스 및 연동 기능 등을 구조적으로 접근하여 테스트한다

시각에 따른 테스트

- **검증(Verification) 테스트** : 제품이 명세서대로 완성되었는지 검증하는 단계이다. 개발자의 시각에서 제품의 생산 과정을 테스트하는 것을 의미한다
- **확인(Validation) 테스트** : 사용자의 요구사항을 잘 수행하고 있는지 사용자의 시각에서 생산된 제품의 결과를 테스트하는 것을 의미한다

---

> ## 26. 테스트 케이스(Test Case)

테스트 케이스 정의

- 구현된 소프트웨어가 사용자의 요구사항을 정확하게 준수했는지를 확인하기 위해 설계된 입력값, 실행 조건, 기대 결과 등으로 구성된 테스트 항목에 대한 명세서를 의미한다
- 테스트의 목표 및 테스트 방법을 결정하고 테스트 케이스를 작성해야 한다
- 테스트 케이스 자동 생성
- 자료 흐름도 -> 테스트 경로 관리
- 입력 도메인 분석 -> 테스트 데이터 산출
- 랜덤 테스트 -> 무작위 값 입력, 신뢰성 검사

---

> ## 27. 블랙박스 테스트 vs 화이트박스 테스트

블랙박스 테스트(Black Box Test)

- 소프트웨어가 수행할 특정 기능을 알기 위해 각 기능이 완벽히 작동되는 것을 입증하는 테스트로 기능 테스트라고 한다
- 대표적인 명세 기반 기법(Specification-based Technique)이다
- 등가 분할의 경계 부분에 해당하는 입력값에서 결함이 발견될 확률이 경험적으로 높아서 결함을 방지하기 위해 경계값까지 포함하여 테스트하는 기법이다
- **종류** : 동치 분할 검사, 원인 효과 그래프, 오류 예측 검사, 비교 검사, 경계값 분석

화이트박스 테스트(White Box Test)

- 모듈의 원시 코드를 오픈시킨 상태에서 코드의 논리적 모든 경로를 테스트하는 방법이다
- Source Code 의 모든 문장을 한 번 이상 수행함으로써 진행된다
- 화이트박스 테스트의 이해를 위해 논리 흐름도(Logic-Flow Diagram)를 이용할 수 있다
- 테스트 데이터를 이용해 실제 프로그램을 실행함으로써 오류를 찾는 동적 테스트(Dynamic Test)에 해당한다
- **종류** : 기초 경로 검사, 루프 테스트, 데이터 흐름 테스트, 제어 구조 검사

---

> ## 28. 알고리즘 순환 복잡도

시간 복잡도 Big-O 표기법

| 분류         | 내용                                                                                 |
|------------|------------------------------------------------------------------------------------|
|O(1)        |상수 시간의 복잡도를 의미하며 입력값 n 이 주어 졌을 때, 문제를 해결하는 데 오직 한 단계만 거친다(해시함수)                                                                                    |
|O(long_{2}n) |시간의 복잡도를 의미하며 입력값 n 이 주어 졌을 때, 문제를 해결하는 데 필요한 단계들이 연산마다 특정 요인에 의해 줄어든다(이진 탐색)                                                                                    |
|O(nlog_{2}n) |선형 로그 시간의 복잡도를 의미하며 문제 해결을 위한 단계수는 nlog2n 번의 수행 시간을 갖는다(큌정렬, 병합(합병)정렬                                                                                     |
|O(n)        |선형 시간의 복잡도를 의미하며 문제를 해결하기 위한 단계의 수와 입력값 n이 1:1 관계이다(순차탐색)                                                                                    |
|O(n^{2})    |제곱 시간의 복잡도를 의미하며 문제를 해결하기 위한 단계의 수는 입력값 n의 제곱근이다(버블 정렬, 삽인 정렬, 선택 정렬)                                                                                    |
|O(C^{n})    |지수 시간의 복잡도를 의미하며 문제를 해결하기 위한 단계의 수는 주어진 사수값 C의 n제곱이다                                                                                    |

---

> ## 29. 소스 코드 최적화

클린 코드(Clean Code)

- 깔끔하게 잘 정리된 코드이다
- 중복 코드 제거로 애플리케이션의 설계가 개선된다
- 가독성이 높아진다
- 버그를 찾기 쉬워지며, 프로그래밍 속도가 빨라진다

외계인 코드(Alien Code)

- 아주 오래되거나 참고문서 또는 개발자가 없어 유지보수 작업이 어려운 프로그램을 의미한다
 
소스 코드 품질 분석 기법

| 분류         |내용   |
|------------|---|
| 정적 분석 도구   | - 소프트웨어를 분석하는 방법의 하나로 소프트웨어를 실행하지 않고 코드 레벨에서 분석하는 방법이다<br/>- 종류 : pdm, cppcheck, checkstyle, FindBugs   |
| 동적 분석 도구   | - 애플리케이션을 실행하여 코드에 존재하는 메모리 누수 현황을 발견하고, 발생한 스레드의 결함 등을 분석하기 위한 도구이다<br/>- 종류 : Avalanche, Valgrind, ValMeter  |

---

> ## 30. 선형/비성형 구조

- **선형 구조** : 큐, 스택, 데크, 리스트, 연결 리스트
- **비선형 구조** : 그래프, 트리, 인접 행렬
- **스택 응용 분야** : 인터럽트의 처리, 수식의 계산, 서브루틴의 복귀 번지 저장, 후위 표현(Post-fix Expression)의 연산, 깊이 우선 탐색

---

> ## 31. 정렬

버블 정렬(Bubble Sort)

- 인접한 데이터를 비교하면서 그 크기에 따라 데이터의 위치를 바꾸어 정렬하는 방법이다
- **최상, 최악 평균 시간 복잡도 : O(n)**
- **최악, 평균 시간 복잡도 : O(n^{2})**

---

> ## 32. 검색

이분 검색 방법

- 탐색 효율이 좋고 탐색 기간이 적게 소요된다
- 검색할 데이터가 정렬되어 있어야 한다
- 비교 횟수를 거듭할 때마다 검색 대상이 되는 데이터의 수가 절반으로 줄어든다
- 대상 범위의 첫 번째 원소의 위치를 Low 로, 마지막 원소의 위치를 High 로 두고서 그 중간 원소의 위치인 Mid 를 (Low + High) / 2로 구한다
- 찾고자 하는 Key 와 중간값을 비교한다
- **Key > 중간값** : Low 를 (Mid+1)로 두고서 계속 수행
- **Key < 중간값** : High 를 (Mid-1)로 두고서 계속 수행
- **Key = 중간값** : 검색 완료

선형 검색

- 원하는 레코드를 찾을 때까지 처음부터 끝까지 차례로 하나씩 비교하면서 검색한다
- 데이터가 모인 집합(배열, 링크드리스트(Linked-List)등)의 처음부터 끝까지 하나씩 순서대로 비교하며 원하는 값을 찾아 내는 알고리즘이다
- 순차 검색이라고도 한다
- **단점** : 단순한 방식으로 정렬되지 않는 검색에 가장 유용하며 평균 검색 시간이 많이 소요된다
- **평균 검색 횟수** : (n+1)/2

깊이 우선 탐색

- 루트 노드(혹은 다른 임의의 노드)에서 시작해서 다음 분기(Branch)로 넘어가기 전에 해당 분기를 완벽하게 탐색하는 방법이다
- 넓게(Wide) -> 탐색하기 전에 깊게(Deep) 탐색하는 것이다

---

> ## 33. DRM(Digital Rights Management)

DRM
- 디지털 콘텐츠의 지식재산권 보호, 관리 기능 및 안전한 유통과 배포를 보장하는 솔루션이다

DRM 기술 요소

- **사용 규칙 제어 기술** : 콘텐츠 식별 체계, 메타 데이터, 권리 표현 기술
- **저작권 보호 기술** : 암호화(Encryption), 키 관리(Key Management), 암호화 파일 생성(Packager),  식별 기술(Identification), 저작권 표현(Right Expression), 정책 관리(Policy Management), 크랙 방지(Tamper Resistance), 인증(Authentication), 인터페이스(Interface), 이벤트 보고(Event Reporting), 사용 권한(Permission)

DRM 시스템 구성 요소

- **콘텐츠 제공자(Contents Provider)** : 콘텐츠 제공하는 저작권자
- **콘텐츠 분배자(Contents Distributor)** : 쇼핑몰 등으로써 암호화된 콘텐츠 제공
- **패키저(Packager)** : 콘텐츠를 메타 데이터와 함께 배포할 수 있는 단위로 묶는 기능
- **보안 컨테이너** : 원본을 안전하게 유통하기 위한 전자적 보안장치
- **DRM 컨트롤러** : 배포된 콘텐츠의 이용 권한을 통제
- **클리어링 하우스(Clearing House)** : 키 관리 및 라이센스 발급 관리



