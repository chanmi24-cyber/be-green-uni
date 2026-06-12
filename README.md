# 그린대학교(Green University) 학사관리 시스템 - MA

<br>

## 프로젝트 소개

그린대학교(Green University) 학사관리 시스템은 학생, 교수, 관리자 3가지 역할을 지원하는 대학교 학사관리 웹 서비스입니다. 회원관리, 강의관리, 수강신청, 출결, 성적, 학과관리 등 대학 운영에 필요한 핵심 기능을 역할별로 분리하여 제공합니다.

본 프로젝트는 그린컴퓨터아트학원 1차 팀 프로젝트로, 2026.03.06 ~ 2026.03.26 (약 3주) 동안 비전공자 4인이 풀스택(Spring Boot + Vue.js)으로 진행했습니다. 백엔드는 MyBatis 기반의 단일 애플리케이션(MA) 구조로 구현했으며, 프론트엔드는 Vue 3로 별도 저장소에서 구현했습니다.

<br>

## Repository 구성

| 구분 | 저장소 |
|---|---|
| Backend (현재 저장소) | [be-green-uni](https://github.com/green-uni/be-green-uni) |
| Frontend | [fe-green-uni](https://github.com/green-uni/fe-green-uni) |

<br>

## 기술 스택

| 구분 | 내용 |
|---|---|
| Backend | Java 21, Spring Boot 4.0.3, Spring Security, MyBatis, JWT, JavaMailSender |
| Database | MySQL |
| Frontend | Vue 3, Vite, Pinia, Vue Router, Axios |
| 협업 도구 | Git, GitHub, Notion, Figma, Google Sheets, ERD Cloud |

<br>

## 패키지 구조

```
src/main/java/com/green/greenuni/
├── configuration/   # 공통 설정 (Security, 예외처리, 상수 등)
└── application/
    ├── member/      # 회원/인증
    ├── admin/       # 관리자 (회원 관리)
    ├── mail/        # 이메일 인증 (비밀번호 재설정)
    ├── major/       # 학과
    ├── lectures/    # 강의
    ├── course/      # 수강신청
    ├── attendance/  # 출결
    ├── grade/       # 성적 (교수용)
    └── mygrade/     # 성적 (학생용)
```

각 도메인 패키지는 Controller / Service / Mapper / model(DTO) 구조로 구성되어 있습니다.

<br>

## 주요 기능

### 회원 / 인증
- 로그인 / 로그아웃
- 액세스 토큰 재발급 (JWT)
- 내 정보 조회 및 수정
- 비밀번호 변경 (로그인 상태)
- 비밀번호 재설정 (이메일 인증 기반)
- 이메일 인증 코드 발송 및 검증
- (관리자) 회원 등록 (엑셀 업로드 포함)
- (관리자) 회원 목록 조회 (페이징)
- (관리자) 회원 상태 일괄 수정

### 학과
- 학과 목록 조회 (회원/강의 생성 시 사용되는 단순 목록)
- 학과 목록 조회 (페이징)
- 학과 등록
- 학과 수정
- 학과 상세 조회
- 교수 목록 조회

### 강의
- 강의 개설 (교수)
- 강의 정보 수정 (교수)
- 담당 교수명 조회
- 건물/강의실 목록 조회
- 내 강의 목록 조회 (교수/관리자/학생)
- 강의 전체 목록 조회 및 상세 조회
- 강의 수강생 정보 조회
- 강의 상태 변경 (관리자)
- 강의 삭제

### 수강신청
- 수강 가능 강의 목록 조회
- 내 수강신청 내역 조회
- 수강신청 등록 / 취소
- 강의별 수강생 목록 조회
- 페이지 수 조회

### 출결
- 강의별 출결 조회
- 출결 등록 및 수정
- 출결 기록 날짜 목록 조회

### 성적
- 강의별 성적 목록 조회 (교수)
- 성적 입력 및 수정 (교수)
- 내 성적 조회 (학생)

<br>

## 팀원 소개 및 역할 분담

| 이름 | GitHub | 담당 도메인 |
|---|---|---|
| [@k28sy](https://github.com/k78sy) (팀장) | 회원 / 인증 |
| [@chanmi24](https://github.com/chanmi24-cyber) | 강의 |
| [@JunLee Lim](https://github.com/junlee-lim) | 학과 / 수강신청 |
| [@YouYoungGeun](https://github.com/qwazsx1346-cyber) | 출결 / 성적 |

> 전원 풀스택(Backend + Frontend) 개발

<br>

## 프로젝트 자료

- ERD: [ERD Cloud](https://www.erdcloud.com/d/Yf5gB5vzKbNFj5Z29)
- 요구사항 명세서 / 테이블 명세서: [Google Sheets](https://docs.google.com/spreadsheets/d/1lL9BIOGijMM75A00ChnGbz-lQZDQlAgicN7mhMpBsUI/edit?usp=sharing)
- 디자인: [Figma](https://www.figma.com/design/V7ybVGSnkFYyvIqkYXrXE8/%ED%95%99%EC%82%AC-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8--1%EC%B0%A8?node-id=382-5&t=uwi6XCCYT0cjMjAp-0)

<br>

## 실행 방법

### 1. 사전 요구사항
- Java 21
- MySQL
- Node.js (프론트엔드용)

### 2. 백엔드 실행
```bash
git clone https://github.com/green-uni/be-green-uni.git
cd be-green-uni
```
프로젝트 루트에 환경변수 파일(`.env`)을 생성하고 DB 접속 정보, 메일 발송 계정, JWT 시크릿 키 등을 설정합니다.
```bash
./gradlew bootRun
```

### 3. 프론트엔드 실행
```bash
git clone https://github.com/green-uni/fe-green-uni.git
cd fe-green-uni
npm install
npm run dev
```

<br>

## 프로젝트 회고

1차 프로젝트는 단일 애플리케이션(MA) 구조로, 브랜치를 팀원 이름 기준으로 나누어 작업했습니다. 백엔드에서는 머지 충돌이 자주 발생하지는 않았지만, 공통 파일이나 유사한 도메인을 함께 다룰 때는 한 팀원의 작업이 끝날 때까지 기다려야 하는 경우가 있었습니다. 또한 커밋 메시지를 간단하게만 작성해, 문제 발생 시 원인을 추적하기 어려운 점이 있었습니다.

데이터베이스 측면에서는 MyBatis 환경에서 테이블 구조를 HeidiSQL로 직접 수정하다 보니, 쿼리가 점점 길어지고 관리가 번거로워졌습니다. 또한 여러 팀원이 동시에 데이터를 다루는 과정에서 `AUTO_INCREMENT` 값이 충돌하는 문제도 발생했습니다.

이러한 경험을 바탕으로 2차 프로젝트에서는 다음과 같이 개선했습니다.

- 브랜치를 팀원이 아닌 도메인 기준으로 분기하여, 작업 단위를 명확히 구분
- 커밋 메시지를 상세히 작성해, 변경 이력 추적이 가능하도록 개선
- JPA 도입으로 엔티티 중심 설계를 적용해, 테이블 변경 시 직접 SQL을 수정하는 부담을 줄임
- MSA 전환을 통해 도메인별 서비스를 분리, 팀원 간 작업 독립성 확보

> 2차 프로젝트(JPA + MSA 전환): [be-msa-green-uni](https://github.com/green-uni/be-msa-green-uni)
