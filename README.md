# 그린대학교 학사 시스템 BE (Green University Academic System)
> 대학교 학사 관리 백엔드 시스템 - 1차 프로젝트

<br>

## 프로젝트 소개
대학교 학사 업무(강의 개설, 승인, 수강신청, 출석, 성적 등)를 MA(Monolithic Architecture)로 구현한 백엔드 프로젝트입니다.

<br>

## 개발 기간
- 2026.03.10 ~ 2026.03.26 (약 2주간)
- 팀원 4명

<br>

## 기술 스택
| 분류 | 기술 |
|------|------|
| Language | Java |
| Framework | Spring Boot |
| ORM / SQL Mapper | JPA, MyBatis |
| Database | MySQL |
| 인증 | Spring Security, JWT |
| Build Tool | Gradle |

<br>

## 내가 맡은 파트

### 강의 목록 API
- 승인된 전체 강의 목록 조회 (연도·학기별)
- 교수: 내가 개설한 강의를 승인 상태(대기/승인/반려)별 조회
- 학생: 내가 수강신청한 강의 조회
- 관리자: 전체 강의를 상태별·연도학기별 조회

### 강의 개설 API
- 교수가 강의 정보(강의명, 학점, 정원, 강의실 등) 등록
- 강의 시간 및 강의실 중복 시 예외 처리

### 강의 승인·반려 API (관리자)
- 대기 중인 강의 승인 또는 반려 처리
- 상태 전환 플로우 구현 (대기 → 승인 / 대기 → 반려)

### 공통
- 담당 메서드 `@PreAuthorize` 적용 — 권한별 접근 제어
- 담당 쿼리 MyBatis XML 작성

<br>

## 레포지토리
> 프론트엔드 레포지토리: [fe-green-uni](https://github.com/chanmi24-cyber/fe-green-uni)
