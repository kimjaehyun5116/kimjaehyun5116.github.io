---
title:  [IntelliJ] 유용한 인텔리제이 단축키 모음(win)
categories: Intellij
tags: [intellij]
toc: true
toc_sticky: true
date: 2024-05-17
last_modified_at: 2024-05-17
---

![intellij](/assets/images/Intellij.png)

## IntelliJ 유용한 단축키(win)

> ### 1. 네비게이션 단축키 (41개)

| Ctrl + B |         선언부로 이동          |     Ctrl + Alt + H     |          호출 계층 구조          |        Alt + ← + →        |   이전 / 다음 에디터로 이동   |     Ctrl + F12     |     파일 구조     | Alt + 1 |   프로젝트 창 열기   |
|:--------:|:------------------------:|:----------------------:|:--------------------------:|:-------------------------:|:-------------------:|:------------------:|:-------------:|:-------:|:-------------:|
| Ctrl + E |         최근 파일 열기         |     Ctrl + Alt + U     |       Show UML popup       |       Ctrl + [ + ]        |   코드 블록 처음 / 끝 이동   |     Alt + F12      |     터미널 창     | Alt + 2 | Favorite 창 열기 |
| Ctrl + N |         클래스로 이동          |    Ctrl + Shift + B    |         타입 선언부 이동          | Ctrl + Shift + Back Space |    최근 편집 위치로 이동     | Ctrl + Shift + F12 |   모든 툴창 숨기기   | Alt + 3 |   Find 창 열기   |
| Ctrl + G |        코드 라인으로 이동        |    Ctrl + Shift + H    |         메소드 계층 구조          |            ESC            |    툴창에서 에디터로 이동     |         F2         |   이전 이슈로 이동   | Alt + 4 | 실행 창 열기|
| Ctrl + H |         타입 계층 구조         |    Ctrl + Shift + I    | Quick definition(선언부 미리보기) |        Ctrl + Tab         |      Switcher       |     Shift + F2     |   다음 이슈로 이동   | Alt + 5 |디버깅 창 열기|
| Ctrl + Q |      Quick document      |    Ctrl + Shift + N    |           파일로 이동           |            F4             |   Jump to Source    |      윈도우 미지원       | 이전 편집 지점으로 이동 | Alt + 6 |Problems 창 열기|
| Ctrl + U | Super 메소드 / Super 클래스 이동 | Ctrl + Alt + Shift + N |           심볼로 이동           |        Shift + F4         | Jump to Type Source |      윈도우 미지원       |   활성화 창 숨기기   | Alt + 7 |Structure 창 열기|
| Ctrl + B |         구현부로 이동          |      Alt + ↑ + ↓       |      이전 / 다음 메소드로 이동       |            F12            |     이전 툴창으로 이동      |      윈도우 미지원       |   뒤로 / 앞으로    | Alt + 8 |Service 창 열기|
||||||||| Alt + 9 |   Git 창 열기    |

> ### 2. 디버깅 단축키 (14개)

|    F7     |                 Step Into                 |     Alt + F10     | Run Debugging Actions Show Execution Point |
|:---------:|:-----------------------------------------:|:-----------------:|:------------------------------------------:|
|    F8     |                 Step Over                 | Ctrl + Shift + F8 |               Breakpoints 보기               |
|    F9     |              Resume Program               | Alt + Shift + F7  |              Force Step Into               |
| Ctrl + F2 |                  디버깅 종료                   | Alt + Shift + F8  |              Force Stop Over               |
| Ctrl + F5 |                 이전 디버깅 실행                 |    Shift + F8     |                  Step Out                  |
| Ctrl + F8 |              Break Point 걸기               |      Alt + 5      |               디버깅 창 보기 / 숨기기               |
| Alt + F8  | Run Debugging Actions Evaluate Expression |      윈도우 미지원      |                 에디더 디버깅 실행                 |

> ### 3. 코드 생성 단축키 (19개)

|       Ctrl + O       |           Override 메소드 자동완성           |   Shift + Ctrl + /   |         블록 주석 처리         |
|:--------------------:|:-------------------------------------:|:--------------------:|:------------------------:|
|       Ctrl + I       |          Implement 메소드 자동완성           |     Alt + Enter      |           퀵픽스            |
|    Ctrl + Alt + J    |      Surround with live template      |     Alt + Insert     |          코드 생성           |
|    Ctrl + Alt + L    |             Reformat code             |     Ctrl + Space     |         기본 자동 완성         |
|    Ctrl + Alt + T    |             Surround with             | Ctrl + Space + space |     Static 메소드 자동완성      |
| Ctrl + Shift + Enter |         Statement completion          | Ctrl + Shift + Space |        스마트 자동 완성         |
|       Ctrl + J       |                라이브 템플릿                |         prsf         |   Private Static Final   |
|     psvm + main      | Public Static Void Main(String[] Arg) |         prf          |   Public Static Final    |
|         sout         |         System.out.println()          |        const         | Private Static Final Int |
|       Ctrl + /       |                 주석 처리                 ||                          |

> ### 4. 편집 단축키 (28개)

|        Ctrl + D        |        라인 복사        |          F6          |       Move       |
|:----------------------:|:-------------------:|:--------------------:|:----------------:|
|        Ctrl + I        | Implement 메소드 자동완성  |      Ctrl + F6       | Change signature |
|        Ctrl + O        |  Overrid 메소드 자동완성   |      Shift + F6      |     이름 일괄 변경     |
|        Ctrl + R        |     파일 내 키워드 대체     |  Ctrl + Shift + F6   |     타입 일괄 변경     |
|        Ctrl + Y        |        라인 삭제        |       Ctrl + /       |       주석처리       |
|     Ctrl + Alt + F     |   Introduce field   |   Shift + Ctrl + /   |      블록주석처리      |
|     Ctrl + Alt + I     |       다오 인텐트        |         Tab          |       인텐트        |
|     Ctrl + Alt + N     |       Inline        |     Shift + Tab      |       역인텐트       |
|     Ctrl + Alt + O     |     import 최적화      |     Ctrl + Space     |     기본 코드 완성     |
|     Ctrl + Alt + P     | Introduce parameter | Ctrl + Space + Space | Static 메소드 자동완성  |
|     Ctrl + Alt + V     | Introduce variable  |     Alt + Insert     |      코드 생성       |
|    Ctrl + Shift + R    |     경로 내 키워드 대체     |     Alt + Enter      |       퀵픽스        |
| Ctrl + Alt + Shift + T |    Refactor this    | Shift + Ctrl + Enter |       구문완성       |
|    Alt + Shift + up    |      라인 위로 이동       |  Alt + Shift + Down  |    라인 아래로 이동     |

> ### 5. 기능 단축키 (4개)

|  Ctrl + Alt + S  | Settings / Preferences |
|:----------------:|:----------------------:|
| Shift + Ctrl + A |      Find Action       |
|Ctrl + Alt + Insert |파일생성 (에디터에서)|
|Alt + Insert|파일생성 (프로젝트 창에서)|

> ### 6. 검색 단축키 (4개)

|   Ctrl + F    |    현재 파일에서 검색    |
|:-------------:|:----------------:|
|   Ctrl + E    |   최근 열었던 파일 목록   |
| Shift + Shift |      전체 검색       |
|   Alt + F7    | 해당 항목이 사용된 위치 검색 |


> ### 7. Git 단축키 (5개)

|     Ctrl + K     |         Commit          |
|:----------------:|:-----------------------:|
|     Ctrl + T     | Update project from VCS |
| Ctrl + Shift + K |          Push           |
|     Alt + `      |        Git 기능 모음        |
|     Alt + 9      |        Git 창 열기         |

> ### 8. 기본 단축키 (11개)

| Ctrl + A |  전체 선택   |      Ctrl + Z       |      실행취소      |
|:--------:|:--------:|:-------------------:|:--------------:|
| Ctrl + C |    복사    |       Alt + 1       | 프로젝트 창 열기 / 닫기 |
| Ctrl + S |    저장    |    Ctrl + ← + →     |     단어별 이동     |
| Ctrl + V |   붙여넣기   |     Home + End      |  라인 처음 / 끝 이동  |
| Ctrl + W | 선택 영역 확장 | Page Up + Page Down | 페이지 위 / 아래 이동  |
| Ctrl + X |   잘라내기   |                     |                |

> 9. 실행 단축키 (13개)

|     Ctrl + F      |     최근 디버깅 실행     | Ctrl + Shift + F10 | Run Edit configuration |
|:-----------------:|:-----------------:|:------------------:|:----------------------:|
|     Ctrl + F2     |        종료         | Alt + Shift + F10  | Run Edit configuration |
|     Ctrl + F9     |        빌드         |      Alt + F9      |     Run to cursor      |
|    Ctrl + Ctrl    |   Run anything    |     Alt + F10      |  Show Execution point  |
|  Ctrl + Alt + F5  | Attach to process |    Shift + F10     |           실행           |
| Ctrl + Shift + F9 | Recompile Project |                    |                        |
