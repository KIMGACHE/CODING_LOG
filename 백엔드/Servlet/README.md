## Servlet
**Servlet** : 다양한 클라이언트 요청에 의해서 동적인 content로 응답가능한 자바 기반의 웹 컴포넌트. <br>

### Servlet Mapping
1. web.xml에 등록하는 방법
이클립스 프로젝트를 우클릭하여 Java EE Tools-Generate Deployment Descriptor Stub클릭하면 WEB-INF폴더안에 web.xml파일이 생성된다.<br>
**web.xml파일은 Java 웹 어플리케이션의 설정파일로, 서블릿 컨테이너에서 웹 어플리케이션이 어떻게 동작할지를 정의하는 역할을 한다.**<br>
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

### Filter
필터는 웹과 관련된 공통 관심사(로그인, 사용자 권한)를 처리할 때 주로 사용된다. <br>
기본적으로 필터는 dispatcherServlet이전에 호출되고, 체인으로 구성되어 여러 개의 필터를 자유롭게 추가할 수 있다.<br>
이때, 필터에서 적절하지 않은 요청이라고 판단하면 dispatcherServlet을 호출하지 않고 요청을 끝낼 수도 있다. <br>
(HTTP요청 -> WAS -> Filter1 -> Filter2 -> Filter3 -> Dispatcher Servlet -> Controller)<br>
<br>
필터는 3가지 메서드로 구성된다.
1. init() : 필터 초기화 메서드, Servlet 컨테이너가 생성될 때 호출된다.
2. doFilter() : 고객의 요청이 올 때마다 메서드가 호출된다. 필터의 로직을 구현하는 메서드이다.
   - doFilter()메서드는 파라미터에 FilterChain을 가지는데 filterchain.doFilter(request,response)메서드를 호출할 수 있다.
   - 다음 필터가 있으면 필터를 호출하고 필터가 없으면 dispatcherServlet을 호출한다.
   - 이 로직을 호출하지 않으면 다음 단계로 진행되지 않기때문에 특별한 경우를 제외하고 반드시 호출해야 한다.
4. destroy() : 필터 종료 메서드, Servlet 컨테이너가 종료될 때 호출된다.

```
@WebFilter("/*")
public class UTF8_EncodingFilter implements Filter {
@Override
public void doFilter(ServletRequest servletRequest, ServletResponse servletReponse, FilterChain filterChain) throw Exception {
	doChain(servletRequest, servletResponse);
}
}
```
매개변수로 ServletRequest와 ServletResponse를 받으며 이를 각각 HttpServletRequest, HttpServletResponse로 다운캐스팅하여 사용할 수 있다. <br>
**@WebFilter** <br>
1. /* : 모든 url의 요청에 대해 처리한다.
2. *do : 확장자가 do인 모든 요청에 대해 처리한다.(do는 임의로 지정한 확장자, 무엇이 들어가든 상관없다)
3. * : 단독으로 사용 불가, 보통 확장자 매핑과 함께 사용
<br>
Filter또한 Mapping이 가능하며 Servlet과 완전히 동일한 방식을 사용한다.
```
<filter>
  	<filter-name>UTF_8_Filter</filter-name>
  	<filter-class>Filter.UTF8_EncodingFilter</filter-class>
</filter>
<filter-mapping>
	<filter-name>UTF_8_Filter</filter-name>
	<url-pattern>/*</url-pattern>  
</filter-mapping>
```

### Listener
특정 이벤트가 발생하기를 기다리다가 실행되는 컴포넌트(메서드나 함수)를 말한다. <br>
**Servlet/JSP 리스너 종류** <br>
1. ServletContext
   - ServletContextListener : 웹 어플리케이션의 시작, 종료이벤트에 대한 이벤트 리스너.
   - ServletContextAtrributeListener : ServletContext에 attribute를 추가하거나 제거, 수정됐을 때에 대한 이벤트 리스너.
3. HttpSession
   - HttpSessionListener : Http세션의 시작, 종료 이벤트에 대한 이벤트 리스터.
   - HttpSessionAttributeListener : HttpSession에 attribute를 추가하거나 제거, 수정됐을 때에 대한 이벤트 리스너.
5. ServletRequest
   - ServletRequestListener : 클라이언트로부터의 요청으로 인한 ServletRequest생성과 응답 이후 ServletRequest제거시에 대한 이벤트 리스너
   - ServletRequestAttributeListener : ServletRequest에 attribute를 추가하거나 제거, 수정됐을 때에 대한 이벤트 리스너.

해당 리스너를 implements하고 메서드를 재정의하여 사용할 수 있다.

### Resource

