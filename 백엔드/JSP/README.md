## JSP
**JSP 스크립트 요소** <br>
- 선언문 : JSP > Servlet으로 변환이 되어 JVM에 의해 컴파일된다. 선언문은 Servlet내에서 **멤버변수, 멤버메서드**를 정의할 수 있다.
- 스크립틀릿 : Service라는 이름의 함수내에서 동작한다. **절차지향 문법**을 적용하려면 스크립틀릿을 사용해야 한다.
- 표현식 : 변수,계산식, 함수 호출 결과를 문자열 형태로 출력한다.
- 지시어 : JSP페이지의 속성을 지정
```
<%@ page import="java.util.*, java.sql.*" %> 지시어를 통해 라이브러리를 import
<%!
  String name = "HONH GIL DONG";
  public String testFunc() {
    System.out.println("선언문 TEST");
  }
%> 선언문을 통해 멤버변수와 멤버메서드를 선언함.
<%= name %> 표현식을 통해 name이라는 변수를 문자열 형태로 출력
<%
  String str1 = "HELLO01";
  String str2 = "HELLO02";
  String str3 = str1+str2;
//Scriptlet은 Service라는 함수내에서 동작하기 때문에 지역변수 선언, 반복문/분기문 처리가 가능하다.
//하지만 함수를 벗어나면 지역변수는 소멸되기 때문에 새로고침시 상태값이 초기화된다.
%>
```

<br>

### Request
Client가 GET이나 POST방식으로 Server에게 요청을 보낼 때 요청객체가 생성되고 이를 통해 값을 전달할 수 있다.<br>
POST의 경우 Query에 요청객체의 값이 나타나지않는다.
```
<form action="C01Request.jsp"> (디폴트값이 method="GET"이다.)
		<input type="text" name="username"/><br>
		<input type="text" name="password"/><br>
		<input type="text" name="bg"/><br>
		<button>전송</button>
</form>
(C01REQUEST_GET.html)
```

```
  String username = request.getParameter("username");
  String password = request.getParameter("password");
  String bgColor = request.getParameter("bg");

<body bgColor=<%=bgColor.equals("") ? "gray" : bgColor %>>
	<h1>요청 결과 확인</h1>
	USERNAME = <%=username %><br>
	PASSWORD = <%=password %><br>
</body>
(C01Request.jsp)
```

### 세션-쿠키-토큰
**세션Session** : 클라이언트의 고유 정보를 담는 객체. 클라이언트의 수만큼 세션 객체가 생성되므로 무거운 데이터를 넣지않는게 권장된다. 서버에 저장됨
```
session.setAttribute("username", "KIMGACHE"); // 키-밸류의 쌍으로 세션의 사용자 인증정보를 저장할 수 있다.
session.setMaxInactiveInterval(60); // 세션유지 기간을 설정할 수 있다. 초단위로 입력하고 기본값은 1800초이다.
session.getAttribute("username); // 키값을 통해 밸류값을 가져올 수 있다.
session.getMaxInactiveInterval(); // 세션유지 기간을 가져올 수 있다.
session.invalidate(); // 세션의 값을 제거하고 삭제한다.
```
**쿠키Cookie** : 세션의 정보들 중 덜 중요한 정보를 클라이언트의 브라우저에 저장한다.
문자열 데이터만 저장가능, 4Kbyte이하의 공간을 차지, 여러개의 쿠키를 설정가능하다(최대 300개), 도메인당 20개까지 저장가능,
저장한도를 초과하면 최근에 사용되지 않는 쿠키부터 자동으로 삭제된다.
```
Cookie cookie1 = new Cookie("myCookie1","myCookie1Value");
```

**토큰Token** : 쿠키는 브라우저에 저장되므로 보안이 취약하여 쿠키를 암호화한 것이 토큰이다.


