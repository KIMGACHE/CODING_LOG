## JAVA

### MVC패턴
MVC패턴은 사용자 인터페이스, 데이터 및 논리 제어를 구현하는데 널리 사용되는 소프트웨어 디자인 패턴입니다. <br>

Model : 처리할 데이터에 대한 정보? <br>
Controller : 파라미터 받기, 유효성 체크, 서비스 요청, 뷰로 결과전달 <br>
View :  사용자로부터 요구사항 전달받기? <br>

### 파일구조
Controller : View로 전달되는 요구사항 처리 <br>
View : 사용자 UI <br>
Domain : 유스케이스 Actor별 기능 Model 정의 <br>
  common : 공통 관심사(Dao, Dto, Service) <br>
    Dao : Data Access Object, 테이블 CRUD <br>
    Dto : Data Transfer Object, 저장단위 <br>
    Service : 비즈니스 로직 <br>
  User(x) : 회원전용 <br>
  Member(x) : 사서전용 <br>
  Admin(x) : 관리자전용 <br>
Dependencies : 의존 처리 폴더(lib) <br>
Properties : 전역 설정 파일(application.properties) <br>

### 흐름
1. Presentation Layer
   -FrontController
     - map("endPoint", SubController객체)
     - init() : 연결한 SubController객체 초기화
     - execute() : View로부터 파라미터를 받아 SubController 실행
   -SubController(Interface)
     - execute() : 하위 컨트롤러가 재정의하도록 유도
   -BookController
     - execute() : 파라미터 받기, 유효성 체크, 서비스 실행, 뷰로 이동/내용 전달
   -UserController
     - execute() : 파라미터 받기, 유효성 체크, 서비스 실행, 뷰로 이동/내용 전달
3. Persistence Layer
4. Business Layer


























