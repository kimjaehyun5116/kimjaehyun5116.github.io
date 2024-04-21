---
title:  "Oracle_setup_setting(오라클 설치 및 셋팅)"

categories:
  -  DB
tags:
  - [Server, SQL, DB, Oracle]

toc: true
toc_sticky: true

date: 2024-05-23
last_modified_at: 2024-05-23
---

![oracle.png](/assets/images/oracle.png)

## 오라클 데이터베이스 설치
- 설치버전 : Oracle 11g XE
- 다운로드 경로 :
- [Oracle Database XE 다운로드 페이지](https://www.oracle.com/database/technologies/xe-prior-release-downloads.html)

#### 설치과정

![oracle1.png](/assets/images/oracle1.png)

![oracle2.png](/assets/images/oracle2.png)

![oracle3.png](/assets/images/oracle3.png)

#### 아래의 system 계정의 패스워드는 'adminuser' 로 넣으세요

![oracle4.png](/assets/images/oracle4.png)

#### 아래의 install 을 누르면 설치가 시작됩니다

![oracle5.png](/assets/images/oracle5.png)

![oracle6.png](/assets/images/oracle6.png)

#### 설치가 완료되면 finish 를 눌러 설치를 마칩니다

![oracle7.png](/assets/images/oracle7.png)

#### 오라클 사용자 계정 추가
#### 먼저 command 창을 엽니다

![oracle8.png](/assets/images/oracle8.png)

#### 열린 화면에서 sqlplus 를 입력합니다

![oracle9.png](/assets/images/oracle9.png)

#### 물어보는 사용자 계정에
#### user name : system
#### password : adminuser 를 입력합니다
#### 이때 password 입력시 커서가 움직이지 않고 입력이 안되는 것처럼 화면이 나오지만 입력이 안되는 것이 아니니까 개념치 말고 입력하면 됩니다

![oracle10.png](/assets/images/oracle10.png)

#### 로그인이 되면 사용자를 생성합니다
#### 사용자 생성 명령 : create user scott identified by tiger;
#### 이때 생성되는 아이디가 scott,  비밀번호가 tiger 입니다
<br>

#### 사용자가 생성되면 권한을 설정합니다
#### 권한 설정 명령 : grant dba to scott;

#### 두 명령을 입력할 때 반드시 마지막에 세미콜론을 입력해주세요

![oracle11.png](/assets/images/oracle11.png)

#### 권한 설정까지 마치면 conn을 입력하고 생성된 계정으로 로그인을 테스트 합니다
<br>

#### 이클립스와 오라클의 연동 (이번 포스팅에서는 이클립스와 연동 해보겠습니다)
#### 이클립스 화면에서 Data Source Explorer 창으로 이동합니다

![oracle12.png](/assets/images/oracle12.png)

#### 해당 윈도우가 없으면 window 메뉴 -> show view -> other 에 가서 해당 창을 찾아 화면에 표시합니다

![oracle13.png](/assets/images/oracle13.png)

![oracle14.png](/assets/images/oracle14.png)

#### Database Connections 에서 마우스 오른쪽 버튼을 누르고 New 를 클릭합니다

![oracle15.png](/assets/images/oracle15.png)

#### Oracle 을 선택하고 Next 를 누릅니다

![oracle16.png](/assets/images/oracle16.png)

#### 나타나는 화면에서 New Driver Definition 을 선택합니다

![oracle17.png](/assets/images/oracle17.png)

#### Oracle thin Driver 11 선택

![oracle18.png](/assets/images/oracle18.png)

#### 기존드라이버 파일은 지우고

![oracle19.png](/assets/images/oracle19.png)

#### 새로운 드라이버 파일 ojdbc6.jar 선택
####  Add JAR/Zip.. 눌러서 파일 선택

![oracle20.png](/assets/images/oracle20.png)

#### 새 파일 경로는 C:\oraclexe\app\oracle\product\11.2.0\server\jdbc\lib

![oracle21.png](/assets/images/oracle21.png)

#### 마지막 탭에서 아래 내용을 수정합니다

![oracle22.png](/assets/images/oracle22.png)

#### OK 를 누르면 아래 화면이 나오는데

![oracle23.png](/assets/images/oracle23.png)

#### save password 체크, Catalog DBA 후 Test Connection 을 눌러서 연결을 테스트 합니다. 이때 Ping Suceeded 가 나와야 정산 연결입니다

![oracle24.png](/assets/images/oracle24.png)

### 요약. IDE 프로그램은 개발에 필요한 다양한 기능을 한 곳에 통합하여 제공하는 소프트 웨어입니다.
<br>
1. Visual Studio (마이크로소프트)<br>
2. IntelliJ IDEA (JetBrains)<br>
3. Eclipse (Eclipse Foundation)<br>
4. PyCharm (JetBrains)<br> 
등이 있으며 포스팅 내용은 그 중 하나인 Eclipse 입니다
<br>

### DB는 "Database"의 약자로 데이터를 구조화하여 저장, 관리하는 시스템을 말합니다.
<br>
1. Oracle Database<br>
2. MySQL<br>
3. PostgreSQL<br>
4. Microsoft SQL Server<br>
등이 있으며 오늘 포스팅 내용은 그 중 하나인 Oracle 입니다


