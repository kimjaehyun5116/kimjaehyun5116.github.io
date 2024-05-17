---
title: "[IntelliJ] 유용한 인텔리제이 단축키 모음(Mac)"
categories: IntelliJ
tags: [IntelliJ]
toc: true
toc_sticky: true
date: 2024-05-17
last_modified_at: 2024-05-17
---

![intellij](/assets/images/Intellij.png)

## IntelliJ 유용한 단축키(Mac)

> ### 1. 네비게이션 단축키 (41개)

|   ⌘ + B   |         선언부로 이동          | ⌃ + ⌥ + H  |          호출 계층 구조          |   ⌃ + ← + →    |   이전 / 다음 에디터로 이동   |    ⌘ + F12     |     파일 구조     | ⌘ + 1 |   프로젝트 창 열기   |
|:---------:|:------------------------:|:----------:|:--------------------------:|:--------------:|:-------------------:|:--------------:|:-------------:|:-------:|:-------------:|
|   ⌘ + E   |         최근 파일 열기         | ⌥ + ⌘ + U  |       Show UML popup       |   ⌘ + [ + ]    |   코드 블록 처음 / 끝 이동   |    ⌥ + F12     |     터미널 창     | ⌘ + 2 | Favorite 창 열기 |
|   ⌘ + O   |         클래스로 이동          | ⌃ + ⇧ + B  |         타입 선언부 이동          | ⇧ + ⌘ + Delete |    최근 편집 위치로 이동     |  ⇧ + ⌘ + F12   |   모든 툴창 숨기기   | ⌘ + 3 |   Find 창 열기   |
|   ⌘ + L   |        코드 라인으로 이동        | ⌘ + ⇧ + H  |         메소드 계층 구조          |      ESC       |    툴창에서 에디터로 이동     |       F2       |   이전 이슈로 이동   | ⌘ + 4 | 실행 창 열기|
|   ^ + H   |         타입 계층 구조         | ⌥  + Space | Quick definition(선언부 미리보기) |    ⌃ + Tab     |      Switcher       |     ⇧ + F2     |   다음 이슈로 이동   | ⌘ + 5 |디버깅 창 열기|
|    F1     |      Quick document      |   ⌘ + ⇧    |           파일로 이동           |     ⌘ + ↓      |   Jump to Source    | ⌘ + ⇧ + Delete | 이전 편집 지점으로 이동 | ⌘ + 6 |Problems 창 열기|
|   ⌘ + U   | Super 메소드 / Super 클래스 이동 | ⌘ + ⌥ + O  |           심볼로 이동           |     ⇧ + F4     | Jump to Type Source |    ⇧ + ESC     |   활성화 창 숨기기   | ⌘ + 7 |Structure 창 열기|
| ⌘ + ⌥ + B |         구현부로 이동          | ⌃ + ↑ + ↓  |      이전 / 다음 메소드로 이동       |      F12       |     이전 툴창으로 이동      | ⌘ + ⌥ + ← + →  |   뒤로 / 앞으로    | ⌘ + 8 |Service 창 열기|
|           ||            ||                ||                || ⌘ + 9 |   Git 창 열기    |

> ### 2. 디버깅 단축키 (14개)

|     F7     |                 Step Into                 |  ⌥ + F10   | Run Debugging Actions Show Execution Point |
|:----------:|:-----------------------------------------:|:----------:|:------------------------------------------:|
|     F8     |                 Step Over                 |   ⌘ + 5    |               디버깅 창 보기 / 숨기기               |
| ⇧ + ⌘ + F8 |              Breakpoints 보기               |   ⌘ + F2   |                   디버깅 종료                   |
|   ⌘ + R    |                 이전 디버깅 실행                 |   ⌘ + F8   |               Break Point 걸기               |
| ⌥ + ⌘ + R  |              Resume Program               |   ⇧ + F8   |                  Step Out                  |
| ⌃ + ⇧ + D  |                에디터 디버깅 실행                 | ⌥ + ⇧ + F8 |              Force Step Into               |
|   ⌥ + F8   | Run Debugging Actions Evaluate Expression | ⌥ + ⇧ + F7 |              Force Stop Over               |

> ### 3. 코드 생성 단축키 (19개)

|    ⌃ + O    |           Override 메소드 자동완성           |     ⌥ + ⌘ + /     |         블록 주석 처리         |
|:-----------:|:-------------------------------------:|:-----------------:|:------------------------:|
|    ⌃ + I    |          Implement 메소드 자동완성           |   ⇧ + ⌘ + Enter   |   Statement completion   |
|  ⌥ + ⌘ + J  |      Surround with live template      |     ⌥ + Enter     |           퀵픽스            |
|  ⌥ + ⌘ + L  |             Reformat code             |     ⌃ + Space     |         기본 자동 완성         |
|  ⌥ + ⌘ + T  |             Surround with             | ⌘ + Space + space |     Static 메소드 자동완성      |
|    ⌘ + N    |                 코드 생성                 |   ⌃ + ⇧ + Space   |        스마트 자동 완성         |
|    ⌃ + J    |                라이브 템플릿                |       prsf        |   Private Static Final   |
| psvm + main | Public Static Void Main(String[] Arg) |        prf        |   Public Static Final    |
|    sout     |         System.out.println()          |       const       | Private Static Final Int |
|  ⌘ + /   |                 주석 처리                 |                   |                          |

> ### 4. 편집 단축키 (28개)

|   ⌘ + D    |        라인 복사        |        F6         |       Move       |
|:----------:|:-------------------:|:-----------------:|:----------------:|
|   ⌃ + I    | Implement 메소드 자동완성  |      ⌘ + F6       | Change signature |
|   ⌃ + O    |  Overrid 메소드 자동완성   |      ⇧ + F6       |     이름 일괄 변경     |
|   ⌘ + R    |     파일 내 키워드 대체     |    ⌘ + ⇧ + F6     |     타입 일괄 변경     |
| ⌘ + Delete |        라인 삭제        |       ⌘ + /       |       주석처리       |
| ⌥ + ⌘ + F  |   Introduce field   |     ⌥ + ⌘ + /     |      블록주석처리      |
| ⌃ + ⌥ + I  |       자동 인텐트        |        Tab        |       인텐트        |
| ⌥ + ⌘ + N  |       Inline        |      ⇧ + Tab      |       역인텐트       |
| ⌃ + ⌥ + O  |     import 최적화      |     ⌃ + Space     |     기본 코드 완성     |
| ⌥ + ⌘ + P  | Introduce parameter | ⌘ + Space + Space | Static 메소드 자동완성  |
| ⌥ + ⌘ + V  | Introduce variable  |       ⌘ + N       |      코드 생성       |
| ⌘ + ⇧ + R  |     경로 내 키워드 대체     |     ⌥ + Enter     |       퀵픽스        |
|   ⌃ + T    |    Refactor this    |   ⇧ + ⌘ + Enter   |       구문완성       |
| ⌥ + ⇧ + ↑  |      라인 위로 이동       |     ⌥ +⇧ + ↓      |    라인 아래로 이동     |

> ### 5. 기능 단축키 (4개)

|   ⌘ + A   | Settings / Preferences |
|:---------:|:----------------------:|
| ⇧ + ⌘ + A |      Find Action       |
| ⌃ + ⌥ + N |파일생성 (에디터에서)|
|   ⌘ + N   |파일생성 (프로젝트 창에서)|

> ### 6. 검색 단축키 (4개)

| ⌘ + F  |    현재 파일에서 검색    |
|:------:|:----------------:|
| ⌘ + E  |   최근 열었던 파일 목록   |
| ⇧ + ⇧  |      전체 검색       |
| ⌥ + F7 | 해당 항목이 사용된 위치 검색 |


> ### 7. Git 단축키 (5개)

|   ⌘ + K   |         Commit          |
|:---------:|:-----------------------:|
|   ⌘ + T   | Update project from VCS |
| ⌘ + ⇧ + K |          Push           |
|   ⌃ + V   |        Git 기능 모음        |
|   ⌘ + 9   |        Git 창 열기         |

> ### 8. 기본 단축키 (11개)

| ⌘ + A |  전체 선택   |   ⌘ + Z    |      실행취소      |
|:--------:|:--------:|:----------:|:--------------:|
| ⌘ + C |    복사    |   ⌘ + 1    | 프로젝트 창 열기 / 닫기 |
| ⌘ + S |    저장    | ⌥ + ← + →  |     단어별 이동     |
| ⌘ + V |   붙여넣기   | fn + ← + → |  라인 처음 / 끝 이동  |
| ⌘ + X| 잘라내기 | fn + ↑ + ↓ | 페이지 위 / 아래 이동  |
|  |      |    ⌥ + ↑ + ↓    | 선택 영역 확장 / 축소  |

> 9. 실행 단축키 (13개)

|   ⌘ + F    |     최근 디버깅 실행     | ⌘ + ⇧ + F9 |     Recompile Project     |
|:----------:|:-----------------:|:----------:|:-------------------------:|
|   ⇧ + D    |    에디터 디버깅 실행     | ⌃ + ⇧ + R  | Run context configuration |
|   ⌘ + F2   |        종료         | ⌃ + ⌥ + R  |  Run Edit configuration   |
|   ⌘ + F9   |        빌드         |  ⌥ + F10   |   Show Execution point    |
|   ⌃ + ⌃    |    Run anyting    |  ⌥ + F10   |       Run to cursor       |
| ⌥ + ⇧ + F5 | Attach to process |   ⌃ + R    |            실행             |
|||   ⌘ + 4    |          실행창 열기           |