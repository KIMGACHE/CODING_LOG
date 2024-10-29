## Servlet
**Servlet** : 다양한 클라이언트 요청에 의해서 동적인 content로 응답가능한 자바 기반의 웹 컴포넌트. <br>

**Servlet Mapping** <br>
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









