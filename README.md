# MVC 패턴 기반 웹 게시판 시스템
> **Java Servlet, JSP, H2 Database를 활용한 사용자/관리자 통합 게시판 서비스**

본 프로젝트는 **MVC(Model-View-Controller) 아키텍처**를 실전 적용하여 데이터베이스 연동 및 비즈니스 로직 처리 과정을 구현한 웹 애플리케이션입니다. 사용자 계정 관리부터 게시글의 CRUD, 첨부파일 업로드 및 관리자 전용 제어 기능을 포함하고 있습니다.

---

## 서비스 흐름 및 화면 설계
사용자의 이용 흐름과 시스템의 계층 구조를 한눈에 파악할 수 있도록 설계하였습니다.

<img width="546" height="306" alt="image" src="https://github.com/user-attachments/assets/fd87e5b4-00e1-4b39-be6f-88cee1f68ede" />

* **사용자(User)**: 로그인 후 게시글 작성, 조회, 검색 및 본인 정보 수정 가능
* **관리자(Admin)**: 전체 회원 정보 및 게시글에 대한 강력한 관리 권한 보유
* **기능적 계층**: UI(JSP) - 컨트롤러(Servlet) - 로직/DB(DAO)의 명확한 역할 분리

---

## 주요 기능
### 1. 회원 및 인증 관리 (User & Auth)
* **가입 및 로그인**: 사용자 가입 기능 및 세션 기반의 로그인 시스템 구축
* **접근 제어**: 로그인한 사용자만 게시판 접근이 가능하며, 본인 게시물에 대한 수정/삭제 권한 부여
* **회원 관리**: 관리자 전용 페이지를 통한 회원 정보 조회 및 강제 삭제 기능
  
### 2. 게시판 시스템 (Board System)
* **게시글 CRUD**: 게시글의 작성, 목록 조회, 상세 보기, 수정, 삭제 기능 구현
* **파일 업로드/다운로드**: 게시글 작성 시 최대 3개의 파일 첨부 지원 및 다운로드 서블릿 구현
* **검색 및 페이징**: 제목, 내용, 작성자 기준 검색 기능과 10개 단위의 효율적인 페이징 처리

---

## 기술 스택
* **Language**: Java 17, JSP, HTML5, CSS3, JavaScript
* **Backend Framework**: Jakarta Servlet (MVC Pattern)
* **Database**: H2 Database (In-memory/File)
* **Library/API**: JSTL, Apache Tomcat 10, JDBC, DBCP (Database Connection Pool)

---

## 아키텍처 (MVC 모델)
프로젝트는 역할 기반으로 폴더 구조를 체계화하였습니다.
* **Model**: 데이터 처리 및 비즈니스 로직 (`com.wplab.service`)
* **View**: 사용자 인터페이스 및 JSP 페이지 (`webapp`)
* **Controller**: 요청 처리 및 흐름 제어 (`com.wplab.post`, `com.wplab.user`)

---

## 🖼️ 실행 화면 요약

### [핵심 화면]
1. **게시판 목록**: 페이징과 검색 바가 적용된 메인 화면
<img width="546" height="116" alt="image" src="https://github.com/user-attachments/assets/f6f0f3fa-eb50-4974-9bb4-cc8950e03c35" />

2. **게시글 상세보기**: 본인이 작성한 글일 경우 '수정/삭제' 버튼 노출 및 첨부파일 다운로드
<img width="546" height="355" alt="image" src="https://github.com/user-attachments/assets/cb27d25d-3f73-4589-a7d3-5ecba4ff72ff" />


<details>
<summary>기타 실행 화면 보기 (로그인, 회원가입, 관리자 페이지 등)</summary>

* **로그인 화면**: 사용자 인증 및 에러 메시지 처리
<img width="247" height="225" alt="image" src="https://github.com/user-attachments/assets/6aa6d7f4-ba1c-4391-a06d-a8ec783b4002" />  

* **관리자 회원 관리**: 전체 사용자 리스트 조회 및 관리 기능
<img width="546" height="85" alt="image" src="https://github.com/user-attachments/assets/eb831f1e-713b-4c4b-be92-f6a6725ac64d" />  

* **게시글 작성/수정**: 멀티파트 설정을 통한 파일 첨부 폼
<img width="546" height="355" alt="image" src="https://github.com/user-attachments/assets/94bf620e-186c-41eb-af11-6e75a8e9a57b" />

</details>
