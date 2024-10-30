## Servlet
**Servlet** : 다양한 클라이언트 요청에 의해서 동적인 content로 응답가능한 자바 기반의 웹 컴포넌트. <br>

### Servlet Mapping
1. web.xml에 등록하는 방법
이클립스 프로젝트를 우클릭하여 Java EE Tools-Generate Deployment Descriptor Stub클릭하면 WEB-INF폴더안에 web.xml파일이 생성된다.<br>
해당 파일에서 <servlet>,<servlet-mapping>태그를 사용하여 설정할 수 있다. <br>
```
<servlet>
  	<servlet-name>C02Servlet</servlet-name>
  	<servlet-class>Servlet.C02Servlet_Test</servlet-class>
</servlet>

<servlet-mapping>
	<servlet-name>C02Servlet</servlet-name>
  	<url-pattern>/Servlet_Test02</url-pattern>
</servlet-mapping>
```

<servlet>태그를 통해 자바파일(Servlet.C02Servlet_Test)을 servlet으로 설정하고 이름을 C02Servlet으로 한다. <br>
<servlet-mapping>태그를 통해 이름이 C02Servlet인 servlet을 local에서 /Servlet_Test02경로로 접속할 수 있도록 매핑한다. <br>

2. annotation을 이용하는 방법
```
@WebServlet("/Servlet_Test02")
public class MyServlet extends HttpServlet {}
```
annotation을 이용하여 해당 url경로로 들어오는 요청을 처리한다. <br>

### HttpServlet
Servlet을 구현하기 위한 핵심 API로 일반 클래스가 아니라 추상 클래스로 제공된다. <br>
따라서 상속을 받은 뒤 메서드를 override하여 사용한다.
doGet(HttpServletRequest req, HttpServletResponse resp) : 매핑된 경로로 들어온 GET요청을 처리하는 메서드< br>
doPost(HttpServletRequest req, HttpServletResponse resp) : 매핑된 경로로 들어온 POST요청을 처리하는 메서드 <br>

### Filter & 인터셉터
필터와 인터셉터는 웹과 관련된 공통 관심사(로그인, 사용자 권한)를 처리할 때 주로 사용된다. <br>
기본적으로 필터는 dispatcherServlet이전에 호출되고, 필터는 체인으로 구성되어 여러 개의 필터를 자유롭게 추가할 수 있다.<br>
이때, 필터에서 적절하지 않은 요청이라고 판단하면 dispatcherServlet을 호출하지 않고 요청을 끝낼 수도 있다. <br>
(HTTP요청 -> WAS -> Filter1 -> Filter2 -> Filter3 -> Dispatcher Servlet -> Controller)<br>
<br>
필터는 3가지 메서드로 구성된다.
1. init()
2. doFilter()
3. destroy()

```
@Override
public void doFilter(ServletRequest servletRequest, ServletResponse servletReponse, FilterChain filterChain) throw Exception {}
```
매개변수로 ServletRequest와 ServletResponse를 받으며 이를 각각 HttpServletRequest, HttpServletResponse로 다운캐스팅하여 사용할 수 있다.
