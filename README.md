# CODING_LOG
정보처리산업기사 과정평가형 수업내용 기록 <br>
|목차|NCS모듈| | |
|:---|:---|:---|:---|
|SW_BASIC|[네트워크](./SW_BASIC/네트워크)|[미들웨어](./SW_BASIC/미들웨어)|[DB기초](./SW_BASIC/DB기초)|
|개발자 환경구축|[운영체제 기초](./개발자_환경구축/리눅스)|[GIT](./개발자_환경구축/GIT)||
|화면기획|[요구사항분석](./화면기획/요구사항분석)|[유스케이스](./화면기획/유스케이스)|[유스케이스명세서](./화면기획/유스케이스명세서)|
|화면구현|[HTML](./화면구현/HTML)|[CSS](./화면구현/CSS)|[JAVASCRIPT](./화면구현/JS)|
|응용SW엔지니어링|[JAVA](./프로그래밍언어/JAVA)|[JAVA2](./프로그래밍언어/JAVA2)|[JAVA3](./프로그래밍언어/JAVA3)|
|DB엔지니어링|[Oracle](./DB엔지니어링/ORACLE)|||

eclipse다운로드 - web으로 다운받아야함
JSP - Java Server Page
서버와 클라이언트가 내용교환을 할때 어떠한 포맷팅을 통해 주고받는다.
URL(포매팅) : 프로토콜://웹서버주소:포트번호(생략가능)/요청하는자원의경로와이름

1. 클라이언트인 웹 브라우저에서 특정 URL로 요청
2. 요청라인,헤더,몸체로 구성된 요청이 발생
3. .
4. .
5. .

요청라인 - 요청메서드, URL(쿼리스트링), Protocol/Version

ServerSideScript종류 - ASP, PHP, Servlet/JSP
JSP란 : 동적 페이지를 제공하기 위해서 HTML내에 삽입된 Script코드

Servlet란 : JSP이전에 사용되었던 웹페이지 표현방식, JAVA코드안에 HTML코드를 중간에 삽입해서 처리

eclipse web version다운, jdk 11.0.2다운로드, apache tomcat 9버전

드가자마자 해야하는것
window - preference - General - WorkSpace - Text file encoding을 UTF-8인지 확인
File이라고 검색해서 CSS Files, HTML Files, JSP Files를 들어가서 UTF-8인지 확인
window - perspective - open perspective에서 원하는 관점(지금은 web임)

File - New - Other - server검색 - Apache에서 9버전을 찾음 - 그다음 apache경로를 잡아주는데 이때 폴더 내부까지 드가야한다.

아래에 servers를 더블 클릭하면 나온ㄴ 화면에서 port number를 8090으로하고 관리 port는 8091로한다. 그리고 server파일 저장
잘되는지 우클릭하여 start한번해보기

File - new - dynamic project
Target Runtime - apache 9버전
src - main - webapp - web-INF폴더에 외부라이브러리를 넣어줘야한다.
apache 9 경로에 lib에있는 jsp-api.jar와 servlet-api.jar를 web-INT에 넣는다.

src - main - java는 java Resources와 연결되어있다


JSP 스크립트요소
- 선언문 : JSP->Servlet으로 변환이 되어 JVM에 의해 컴파일된다. 선언문은 servlet내에서 멤버변수,멤버메서드를 정의할 수 있다.
- 스크립트릿 : service라는 이름의 함수내에서 동작한다. 절차지향 문법을 적용하려면 스크립트릿
- 표현식 : ??

선언문
1. 멤버 변수 선언
<%!
  String name = " JSPStudy";
%>
2. 멤버메서드 선언
<%!

%>
3. 멤버변수 확인
<%=name%>












































