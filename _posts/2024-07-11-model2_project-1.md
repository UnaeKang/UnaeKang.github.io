---
title : model2 프로젝트 생성
categories : [CRUD, model2]
date: 2024-07-11 20:21:52 +09:00
tags : [crud, til]
---

### 프로젝트 생성 
`환경: Windows11, STS4, Tomcat 10, Java 17`

1. STS 탭 [File] - [New] - [Dynamic Web Project] 선택 
2. Project name 설정 (여기선 guestBook01 사용)
3. Generate web.xml deployment descriptor 선택 후 Finish
4. [Open Associated Perspective] 팝업 No 클릭
5. 생성된 프로젝트 [Properties] 이동 후 아래 내용 확인
    - [Project Facets] Java 버전 17
    - [Java Build Path] - [Libraries] - [MoudulePath] JRE System Library [JavaSE-17]
    - [Modulepath] - \<Add Library...> - [JRE System Library] - [Workspace default JRE] 추가 

### Server 추가
1. Server 탭에서 [New] - [Server] - [Apache] - [Tomcat 버전]
2. Server name 설정 (여기선 guest_book_server_01 사용)
3. 위에서 생성한 프로젝트를 Configured로 Add 후 Finish
4. Server 탭에 생성된 guest_book_server_01의 [Modules] 이동 
   - Server Locations에서 Use Tomcat installation (takes control of Tomcat installation) 체크
   - Server Options에서 publish module contexts to separate XML files 체크
   - Path를 /로 변경, Auto reloading enabled 체크 해제 후 완료

### JDBC driver 추가
1. https://mvnrepository.com/ 접속 후 mariadb-java-client 검색
2. MariaDB Java Client 3.3.x 버전 Files 중 <jar> 다운로드
3. 경로 - src/main/webapp/WEB-INF/lib에 설치한 jar 파일 추가
<br>

### 웰컴파일 생성
`경로 - src/main/webapp/index.jsp `
```html
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
<meta charest="UTF-8">
<title>방명록 작성하기</title>    
</head>
<body>
    <a href="/book">작성하기</a>
</body>
</html>
```
→ *실행 시 처음으로 보여주는 페이지, 작성하기 텍스트 클릭 시 Get 메소드로 /book이라는 요청을 서버에 보낸다.*