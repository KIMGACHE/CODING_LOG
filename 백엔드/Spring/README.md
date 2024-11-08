## Spring

Library
```
컴퓨터 프로그램에서 사용할 수 있는 재사용 가능한 동작의 모음이다.
리소스가 필요한 경우 프로그램이 라이브러리를 호출하여 개발자들은 복잡한 기능을 더 쉽게 구현할 수 있다.
```
<br>

FrameWork
```
개발자들이 애플리케이션을 개발하는 데 사용되는 구조를 제공한다.
일련의 규칙과 구조를 정의하고, 개발자가 애플리케이션을 작성할 때 이러한 규칙과 구조를 따르도록 한다.
보통 여러 컴포넌트와 라이브러리를 포함하며 개발자가 특정 기능을 구현하기 위해 이를 조합하여 사용한다.
액션을 호출할 수 있는 제어권을 가지고 있다.(제어의 역전)
```
<br>

Api(Application Programming Interface)
```
Application : 개발자가 만드는 응용프로그램이나 어떤 서비스를 의미한다.
Programming : 개발
Interface : 접점, 경계면
=> 으용프로그램 개발에 쓰이는 접점
=> 서로 다른 서비스 간에 필요한 접점을 제공하는 것, 서로 다른 응용 프로그램 간에 개발에 필요한 접점을 제공하는 것.
```
<br>

### Spring FrameWork
1. 의존성 주입(Dependency Injection)
   - Spring은 객체 간의 의존성을 주입하는 기능을 제공한다. 객체 간의 결합도를 낮추고 코드의 유연성을 향상시킨다.
3. 제어의 역전(Inversion of Control)
   - Spring은 제어의 역전 원칙을 따르며, 객체의 생명 주기와 의존성 관리를 프레임워크 담당한다. 이를 통해 개발자는 객체의 생성과 관리에 대한 부담을 줄일 수 있다.
5. AOP(Aspect-Oriented Programming)
   - Spring은 관점 지향 프로그래밍을 지원하여 횡단 관심사를 모듈화할 수 있다.
7. Spring MVC(Spring Model-View-Controller)
   - MVC를 통해 요청을 처리하는 Controller, 데이터를 표시하는 View, 비즈니스 로직을 처리하는 Model로 분리하여 개발할 수 있다.
9. Spring Security
    - 보안을 위한 Spring Security Framework를 제공한다. 인증,권한 부여, 보안 설정등을 쉽게 구현할 수 있다.

### Parameter
요청 URI Mapping Annotation
1. RequestMapping : Spring MVC에서 가장 기본적으로 사용되는 Annotation으로 Http요청과 메서드를 매핑한다.
   - value 또는 path : 매핑할 URI패턴을 지정한다
   - method : 요청을 처리할 HTTP메서드를 지정한다. (ex method=RequestMethod.Get)
   - params : 요청의 parameter를 제한한다.
   - headers : 요청의 header를 제한한다.
   - consumes : 요청의 컨텐츠 타입을 제한한다.
   - produces : 응답의 컨텐츠 타입을 제한한다.
3. GetMapping : HTTP GET요청과 메서드를 매핑한다. @RequestMapping(method=RequestMethod.GET)과 동일하다.
4. PostMapping : HTTP Post요청과 메서드를 매핑한다. @RequestMapping(method=RequestMethod.POST)과 동일하다.
5. PutMapping : HTTP Put요청과 메서드를 매핑한다. @RequestMapping(method=RequestMethod.PUT)과 동일하다.
6. DeleteMapping : HTTP Delete요청과 메서드를 매핑한다. @RequestMapping(method=RequestMethod.DELETE)과 동일하다.
