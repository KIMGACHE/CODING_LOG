## JSP
### 세션-쿠키-토큰
**세션Session** : 클라이언트의 고유 정보를 담는 객체. 클라이언트의 수만큼 세션 객체가 생성되므로 무거운 데이터를 넣지않는게 권장된다. 서버에 저장됨
```
session.setAttribute("username", "KIMGACHE"); // 키-밸류의 쌍으로 세션의 사용자 인증정보를 저장할 수 있다.
session.setMaxInactiveInterval(60); // 세션유지 기간을 설정할 수 있다. 초단위로 입력하고 기본값은 1800초이다.
session.getAttribute("username); // 키값을 통해 밸류값을 가져올 수 있다.
session.getMaxInactiveInterval(); // 세션유지 기간을 가져올 수 있다.
```
**쿠키Cookie** : 세션의 정보들 중 덜 중요한 정보를 클라이언트의 브라우저에 저장한다.
**토큰Token** : 쿠키는 브라우저에 저장되므로 보안이 취약하여 쿠키를 암호화한 것이 토큰이다.
