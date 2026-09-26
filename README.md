# Ohouse-Clone (오늘의집 클론 코딩)
> **순수 Java 기반 인테리어 커머스 플랫폼 클론 프로젝트** <br/>
> 프레임워크(Spring) 없이 JSP/Servlet과 JDBC만을 활용하여 구현한 웹 서비스로, <br/>
> 사용자 쇼핑부터 판매자 관리, 최고 관리자의 통합 시스템까지 전체 커머스 프로세스를 구축했습니다.

## 🗓 프로젝트 개요
- **진행 기간:** YYYY.MM ~ YYYY.MM
- **개발 인원:** 팀 프로젝트
- **담당 역할:** 백엔드 비즈니스 로직 및 DB 설계, 마이페이지/판매자/관리자(Admin) 도메인 핵심 기능 개발

## 🛠 기술 스택 (Tech Stack)
### Backend & View (Core)
<img src="https://img.shields.io/badge/java-007396?style=for-the-badge&logo=java&logoColor=white"> <img src="https://img.shields.io/badge/JSP%20/%20Servlet-E34F26?style=for-the-badge&logo=java&logoColor=white"> <img src="https://img.shields.io/badge/JDBC-4479A1?style=for-the-badge&logo=java&logoColor=white"> <img src="https://img.shields.io/badge/Oracle%20Cloud-F80000?style=for-the-badge&logo=oracle&logoColor=white"> 

### Frontend
<img src="https://img.shields.io/badge/javascript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black"> <img src="https://img.shields.io/badge/jQuery-0769AD?style=for-the-badge&logo=jquery&logoColor=white"> <img src="https://img.shields.io/badge/html5-E34F26?style=for-the-badge&logo=html5&logoColor=white"> <img src="https://img.shields.io/badge/css3-1572B6?style=for-the-badge&logo=css3&logoColor=white">

## 🚀 핵심 기능 (Core Features)
1. **메인 페이지 실시간 인기 검색어 및 키워드 검색**
   - 검색창 입력 시 상품 제목과 키워드가 일치하는 연관 상품(최대 2개) 노출
   - 검색 시 `keyword` 테이블을 조회하여, 새로운 검색어면 `INSERT`, 기존 검색어면 `UPDATE`로 카운트를 증가시키는 로직을 통해 실시간 인기 검색어 순위 시스템 구축
2. **마이페이지 배송지 관리 시스템 (회원)**
   - 사용자별 최대 3개까지 다중 배송지 등록 기능 구현
   - 기본 배송지 설정 기능을 통해 결제 시 편의성 제공
3. **판매자 전용 대시보드 및 CS/정산 관리**
   - 판매자 본인이 등록한 상품의 목록 조회 및 판매 중지(상태 변경) 등 CRUD 구현
   - 사용자의 교환 및 반품 요청이 판매자 대시보드에 실시간 노출되도록 CS 연동
   - 관리자가 승인한 판매 대금 정산 내역 및 금액 조회 기능 제공
4. **최고 관리자(Admin) 통합 제어 시스템**
   - **가입 승인 & 권한 제어:** 판매자 가입 시 `pending` 상태로 대기하며, 관리자가 승인/거절을 처리해야만 로그인 가능. 전체 회원/판매자/상품 목록 조회 및 즉각적인 계정 정지 기능 구현
   - **정산 및 마케팅:** 판매자의 정산 요청을 관리자가 최종 승인하여 금액 지급 처리. 신규 쿠폰을 등록하고 '뿌리기' 버튼을 통해 활동 중인 전체 회원에게 일괄 지급하는 쿠폰 발급 기능 구현

## 🧩 개발 전략 및 데이터베이스 설계
- **순수 Java 기반 아키텍처 구현:** Spring 등 프레임워크에 의존하지 않고 순수 JSP, Servlet, JDBC만을 사용하여 웹 생태계의 핵심 동작 원리와 MVC 패턴을 직접 구현했습니다. 
- **Oracle MERGE 문을 활용한 쿼리 최적화:** 실시간 검색어 순위 집계 시, SELECT 후 조건을 분기하는 2-Step 로직 대신 Oracle의 `MERGE INTO` (UPSERT) 구문을 활용하여 데이터베이스 접근 횟수를 줄이고 쿼리 성능을 최적화했습니다.
- **상태(Status) 기반 라이프사이클 통제:** 일반 회원, 판매자, 최고 관리자로 이어지는 3단계 권한 구조를 설계했습니다. 판매자 가입 대기(`pending` -> `approved`) 및 정산 처리 등 복잡한 비즈니스 로직을 DB의 상태 코드로 관리하여 데이터의 무결성을 안정적으로 확보했습니다.
