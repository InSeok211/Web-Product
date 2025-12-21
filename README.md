# MVC 기반 웹 게시판 시스템 (Web Board System)
> **Java Servlet, JSP, H2 DB를 활용한 MVC 패턴 기반의 게시판 서비스**

본 프로젝트는 웹 프로그래밍의 핵심인 **MVC(Model-View-Controller) 아키텍처**를 이해하고, 데이터베이스와 연동된 동적 웹 애플리케이션을 구현하기 위해 제작되었습니다. 사용자 관리부터 게시글의 CRUD, 관리자 기능까지 포함된 통합 시스템입니다.

---

## 주요 기능
### 1. 회원 관리 (User Management)
* **회원가입 및 로그인**: 사용자 가입 및 세션을 활용한 로그인 상태 유지.  
* **회원 정보 수정/삭제**: 본인의 정보 수정 및 관리자에 의한 회원 관리 기능.

### 2. 게시판 기능 (Board Features)
* **게시글 CRUD**: 게시글 작성, 조회, 수정, 삭제 기능.
* **첨부파일**: 게시글 작성 시 최대 3개의 파일 업로드 및 다운로드 지원.
* **검색 및 페이징**: 제목/내용/작성자 기준 검색 및 10개 단위 페이징 처리.

### 3. 보안 및 접근 제어 (Access Control)
* **권한 관리**: 로그인한 사용자만 게시글 작성 가능.
* **작성자 보호**: 본인이 작성한 글 또는 관리자만 수정/삭제 가능.

---

## 서비스 흐름 및 화면 설계
사용자의 이용 흐름을 고려하여 직관적인 UI/UX와 계층적인 메뉴 구조를 설계하였습니다.

* **로그인(Login)**: 시스템 진입을 위한 인증 단계
* **게시판(Board)**: 글쓰기, 검색, 상세 보기(수정/삭제/다운로드) 기능 제공
* **회원 가입(Sign Up)**: 신규 사용자 등록 
* **관리자(Admin)**: 게시판 및 회원 정보를 통합 관리하는 관리자 전용 메뉴
<img width="546" height="306" alt="image" src="https://github.com/user-attachments/assets/aab3165a-6615-4c32-9259-44f3f4a0e5a6" />

---

## 🛠 기술 스택
* **Backend**: Java 17, Jakarta Servlet, JDBC, DBCP (Database Connection Pool)
* **Frontend**: JSP, JSTL, HTML5, CSS3, JavaScript
* **Database**: H2 Database
* **Server**: Apache Tomcat 10
  
---

## 아키텍처 설계 (MVC Model)
* **Model**: 데이터베이스 상호작용 및 비즈니스 로직 처리 (DO, DAO)
* **View**: JSP를 이용한 사용자 인터페이스 제공
* **Controller**: 사용자의 요청을 처리하고 흐름을 제어하는 Servlet

---

## 데이터베이스 스키마
프로젝트는 `User`, `Post`, `Attachment` 세 개의 테이블로 구성되어 있습니다.
```sql
CREATE TABLE "User" (
    user_id VARCHAR(50) PRIMARY KEY,
    password VARCHAR(255) NOT NULL,
    email VARCHAR(100) NOT NULL
);

CREATE TABLE "Post" (
    post_id INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    content TEXT NOT NULL,
    user_id VARCHAR(50),
    FOREIGN KEY (user_id) REFERENCES "User"(user_id)
);

CREATE TABLE Attachment (
    ATTACHMENT_ID INTEGER NOT NULL AUTO_INCREMENT PRIMARY KEY,
    POST_ID INTEGER NOT NULL,
    FILENAME VARCHAR(255) NOT NULL,
    FILE_PATH VARCHAR(255) NOT NULL
);
```

---

## 실행 화면
* **게시글 목록**
<img width="546" height="116" alt="image" src="https://github.com/user-attachments/assets/c746a6a5-bfb6-4f41-b1d0-5a4db92322ac" />

* **글쓰기**
<img width="546" height="215" alt="image" src="https://github.com/user-attachments/assets/31084141-a332-4755-b90f-2df839fca51a" />

* **관리자 회원 관리**
<img width="546" height="85" alt="image" src="https://github.com/user-attachments/assets/a07ee022-761e-4a07-9be4-ae6e1f93dc07" />

