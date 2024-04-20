---
layout: post
title: "MySQL 설치"
date: 2024-04-18
excerpt: "MySQL을 설치해보자!"
tags: [mysql]
comments: true
---

![mysql](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/0b0412a2-b39a-4b9a-80c6-30fcea75aba0)


## MySQL 이란?

- MySQL은 관계형 데이터베이스 관리 시스템(RDBMS)중 하나로, 오픈 소스로 개발된 소프트웨어이다.
- 주로 애플리케이션 개발과 데이터 베이스 관리에 사용된다.
- MySQL은 많은 운영체제에서 사용 가능하며, 빠르고 안정적인 서능을 제공한다
- 확장성이 뛰어나며, 다양한 기능을 지원한다

## MySQL 설치


사이트에 접속해서 아래와 같이 메뉴를 선택한다

![MySQL1](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/6c91cfc1-3cd5-4901-a7c9-f664d760cd14)


선택 후 표시된 하면에서 아래와 같이 download 를 선택한다

![MySQL2](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/bc74174a-f405-436c-b4be-25e388d41855)


다음화면에서 login 이나 sign up 은 선택하지 않고 아래 화면과 같이 no thanks, just start my download 를 선택한다

![MySQL3](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/8f787c3a-394f-4550-a110-f59db870ace1)


그럼 다운로드가 시작되고 다운로드가 완료되면 아래와 같은 파일을 확인할 수 있다

![MySQL4](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/2f5fafbb-524c-490a-befc-44b0a8bc75de)

파일을 더블클릭해서 설치를 한다

</br>

최초화면에서 custom 을 선택한다

![MySQL5](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/482af7ec-c623-49d2-964f-331cacf8f479)

Next 를 클릭하고 표시된 화면에서 MySQL Server 8.0.36 - x64 와 MySQL Workbench 8.0.36 - x64 를 설치하기위해 선택하고 오른쪽 목록으로 옮긴다

![MySQL6](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/8774e0f8-cd1d-4d04-bdde-af6301ec8576)

Next 를 눌러 다음 화면으로 넘어간다
</br> 표시된 하면에서 Execute 를 누르면 두 개의 설치 상태가 Complete 로 변경된다 그리고 다시 Next를 클릭한다

![MySQL7](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/64e421db-b4f5-44e2-abb9-9fdaca9d31a3)


이 후 화면은 별다른 변경없이 Next 만 클릭하되 아래와 같은 화면에서 root 계정의 비밀번호를 입력한다

![MySQL8](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/1622572c-486d-4adb-8f07-62157aeeae51)


비밀번호는 "adminuser"로 해주고 Password strength:Weak 는 비밀번호가 쉬운 번호라는 경고 문구이니 무시하고 next 로 간다
</br> 이후 계속 변경없이 Next 로 가다가 아래 화면에서 Execute 를 누루면 최종 설치가 진행되고 완료 된다

![MySQL9](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/85229fdf-aeb8-44fc-9e2d-53a437495e77)

설치가 완료되면 finish 를 누르고 마무리 한다

![MySQL10](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/c2b5afbf-8fcf-41ef-86c3-845cec320d77)


이후 Next - finish 단계가 한번 더 있지만 별다른 설정없이 진행 하여 마무리 합니다

![MySQL11](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/dc86811f-f2bd-4342-95a1-35a2a8863cf5)


> 중간에 가끔 port 부분에서 오류가 생기는 경우가 있다 !! 확인하고 넘어가자

![MySQL_er](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/c3bf45a6-9ee9-459c-9835-58cc2d12db33)

보통 위 그람과 같이 3306 은 mysql 관련된 포트라서 한번 삭제했음에도 프로세스는 살아있는것인지, 기존에 지웠다 설치했다를 반복하면서 이런 오류가 뜨는경우가 있다
</br>
리소스 모니터 이용하기
- 윈도우의 '시작' 메뉴 검색에서 '리소스 모니터' 를 찾아 실행하거나, 실행창에서 (Windows 키 + R)에 resmon 을 입력한다
- 리소스 모니터의 네트워크 탭으로 이동한 후 '수신 대기 포트' 섹션을 확인한다
- 이곳에서 3306 포트와 연결된 프로세스의 정보를 상세히 확인할 수 있다

![MySQL_er1](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/61ed7b09-e867-4f91-9efc-cbff4ef5acb8)

프로세스 중지

- 작업 관리자(Ctrl + Alt + Delete 에 젤 밑에 메뉴) 를 열고 '세부 정보' 를 눌러서 위에서 확인한 포트와 연결된 프로세스를 선택 한 후
- '작업 끝내기' 를 클릭하여 프로세스를 종료한다
- 이 방법은 일시적으로 포트 충돌 문제를 해결할 수 있지만, 시스템 재시작 후 문제가 재발할 수 있다
- 그렇기 때문에 작업끝내기를 하고 바로 설치를 재시도 하면 된다

![MySQL_er2](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/e2c8a741-1ddc-4bfc-a676-ed049839f4b2)

자 이제 포트 옆에 느낌표가 사라진것을 확인할 수 있다. 다시 위의 순서대로 설치를 마친다

![MySQL_er3](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/3f69e19f-8730-4f06-b8fe-235bfcffb56e)

## MySQL 설정

설치가 완료되면 WorkBench 가 실행된다. 접속할 root 계정을 눌러 접속을 시도한다

![MySQL12](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/be0c79ad-77dd-4b47-b907-9de2a0e1942c)

패스워드(adminuser)를 입력하고 password in vault 도 체크해서 다음 접속시 패스워드 입력을 생략하도록 한다

![MySQL13](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/21ba6a7b-8a39-4c71-ba85-3d55564df5af)

나타나는 화면에서 schema 를 클릭하고 스키마를 추가한다

![MySQL14](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/5219840d-b755-4c47-aae7-29f9ec6cd339)

![MySQL15](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/4b82eeae-4b56-48b8-8b8c-ee0abd75893e)

스키마는 데이터베이스 테이블의 그룹을 설정하는것과 마찬가지이며, 여러 그룹으로 여러 사이트의 데이터베이스를 별도 관리할 수 있다

- name : scott
- Charset / Collation : utf8bv4 / utf8mb4_general_ci

![MySQL16](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/0174bc14-c949-43ce-95e7-f6aa79831e68)

![MySQL17](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/5b7dcae4-ba62-40d8-961c-704c08e4d82f)

이제부터 테이블을 추가하고 데이터 관리를 할 수 있다

## 이클립스에 MySQL 연동
- MySQL 다운로드 화면에서 드라이버 파일을 다운로드 한다

![MySQL18](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/717e7ae0-b868-4dfa-86f7-5d9c9340d85b)

표시된 화면에서 Platform Independent 를 선택하고 zip 파일을 다운도르 한다

![MySQL19](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/587b0ac5-5fb7-4266-836c-fdeb285fb5b5)

Login Sign Up 은 역시 No thanks

![MySQL20](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/659ced80-7c89-46e5-a159-a184079200f8)

다운로드 받은 파일은 압축을 풀어서 찾기 쉬운 폴더(D:\ 최상위 폴더 등)에 저장한다

![MySQL21](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/4bb67fa2-951e-42e7-84ed-a20b4df2c46a)

이클립스의 DataSource Explorer 에서 Database Connection 에서 오른쪽 마우스 누르고 New 를 선택gksek

![MySQL22](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/1e62cde4-8dce-4493-8b9c-1f740755afe6)

첫 번째 선택은 MySQL

![MySQL23](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/d15b9faf-8f48-4554-9d97-0c783d6d19ca)

다음 선택은 New Drvier Definition

![MySQL24](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/a662b346-4506-4744-9922-b6fa3fcec407)

다음은 MySQL JDBC Driver 5.1 선택하고 JAR List 로 이동

![MySQL25](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/f5387f79-5f77-4ae7-84b4-7925bb8df5ea)

기존 파일은 지우고

![MySQL26](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/5df03aa6-6b3a-4ecf-ab46-407aa26b15b6)

다운 받은 드라이버 파일 선택후 Properties로 이동

![MySQL27](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/a6c517e4-b099-4696-bbdd-6895dc11af89)

URL을 아래와 같이(jdbc:mysql://localhost:3306/scott) 수정하고, 패스워드(adminuser) 넣은 후 OK

![MySQL28](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/ca4bc785-c23f-4628-8a86-ce8f0ceb5b10)

이후 화면에서 Test Connection 눌러서 ping Succeeded 가 나오면 연결 성공

![MySQL29](https://github.com/kimjaehyun5116/kimjaehyun5116.github.io/assets/163956223/d9241198-d0ab-4f0c-900e-337e2d7cd7ef)
