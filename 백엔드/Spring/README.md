# Spring

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

## Spring FrameWork
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

## Parameter
**요청 URI Mapping Annotation**
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

```
@Controller
@RequestMapping("/memo")
@Slf4j
public class MemoController {
	
	@GetMapping("/add")
	public void memo_get() {
		log.info("GET /memo/add...");
	}
	
	@PostMapping(value="/add")
	public void memo_post(MemoDto memoDto) {
		log.info("POST /memo/add..." + memoDto);	
	}
}
위의 경우 GET요청이 프로젝트 경로 + "/memo/add"의 경로로 들어오게되면 "GET /memo/add..."이 출력되고
POST요청이 프로젝트 경로 + "/memo/add"의 경로로 들어오게되면 "POST /memo/add..."이 출력된다.
```   
<br>

**요청 파라미터 Mapping Annotion**
1. @RequestParam : Http요청의 파라미터를 메서드의 파라미터와 바인딩한다. URL쿼리 문자열이나 POST요청의 form데이터와 매핑한다.
   - value : 요청파라미터의 이름을 지정한다. 기본값은 메서드 파라미터의 이름과 동일하게 지정된다.
   - required : 파라미터가 존재해야하는가를 지정한다. 기본값은 true이다.
   - defaultValue : 파라미터의 기본값을 지정한다.
   - name : 파라미터의 별칭을 지정한다. 요청에서 사용되는 이름과 메서드의 파라미터 이름이 다를 때 사용한다.
3. @RequestBody : Http요청의 본문(body)을 메서드의 파라미터에 바인딩한다. 주로 JSON또는 XML형식의 데이터를 객체로 변환할 때 사용한다.
4. @PathVariable : URI의 일부를 메서드의 파라미터에 바인딩한다. 주로 RESTful API에서 동적인 URI를 처리할 때 사용한다.
5. @ModelAttribute : 요청의 특정 속성을 메서드의 파라미터로 바인딩한다. 주로 HTML폼 데이터를 모델 객체로 변환할 때 사용한다.

```
@RequestMapping(value="/p01", method=RequestMethod.GET)
	public void p01(@RequestParam(value = "name",required=false) String name) {
		log.info("GET /param/p01..."+name);
}
RequestParam을 통해 들어올 파라미터의 이름으로 받아올 수 있다. required=false로 파라미터가 존재하지 않더라도 상관없도록 지정

@RequestMapping(value="/p05",method=RequestMethod.GET)
	public void p05(@RequestParam(value="name", defaultValue="홍길동") String name) {
		log.info("POST /param/p05..." + name);
}
defaultValue를 지정함으로써 name이라는 파라미터가 입력되지않은 경우에 기본값으로 홍길동을 사용하였다.

@RequestMapping(value="/p08/{name}/{age}/{addr}",method=RequestMethod.GET)
	public void p08(
				@PathVariable String name,
				@PathVariable int age,
				@PathVariable String addr				
   )
{log.info("GET /param/p08..." + name+ " " + age + " " + addr);}
URI의 일부에 파라미터 name을 지정하고 @PathVariable로 파라미터에 바인딩한다.

@PostMapping(value="/p04")
	public void p04(@RequestBody String name) {
		log.info("POST /param/p04..."+name);
}
이 경우 파라미터의 타입을 Application_JSON으로 하여 "{'name':'홍길동'}"을 보내면 @RequestBody를 통해 name을 받아올 수 있다.
```

<br>

**View로 Data전달에 사용되는 클래스**
1. Model : 스프링 MVC에서 가장 일반적으로 사용되는 클래스 중 하나로 컨트롤러 메서드에서 데이터를 View로 전달하는 데 사용한다.
2. ModelAndView : Model과 View를 모두 포함하는 클래스로 ViewResolver가 지정한 View가 아닌 원하는 특정 View를 선택할 수 있다.
3. Map : Model과 유사한 역할을 하는 인터페이스로 컨트롤러 메서드에서 데이터를 View로 전달하는데 사용한다.

## Validation
**WebDataBinder** : 스프링 MVC에서 사용되는 데이터 바인딩과 유효성 검사를 수행하는 클래스이다. <br>
이 클래스는 컨트롤러 메서드의 파라미터를 바인딩하고 유효성을 검사하는 역할을 한다. 주로 폼 데이터를 처리하고 모델 객체에 바인딩하는데 사용된다.
1. @InitBinder : 컨트롤러 클래스 내부에 선언하여, 특정 컨트롤러에 대한 WebDataBinder 초기화한다.
3. @Valid : 컨트롤러 메서드의 파라미터에 사용되며, 해당 파라미터에 대한 유효성 검사를 지정한다.
4. @Validated : 클래스나 그룹에 대한 유효성 검사를 수행하는데 사용된다.

```
@InitBinder
	public void dataBinder(WebDataBinder webDataBinder) {
		log.info("Phone's dataBinder...");
		webDataBinder.registerCustomEditor(String.class,"phone", new phoneBinder());
		webDataBinder.registerCustomEditor(LocalDate.class,"birthday", new dayBinder());
}
@Slf4j
	private static class dayBinder extends PropertyEditorSupport {
		
		@Override	
		public void setAsText(String dateTest) throws IllegalArgumentException {
			if(dateTest.isEmpty()) {
				dateTest = LocalDate.now().toString();
			} else {
				dateTest = dateTest.replaceAll("~","-");
			}
			LocalDate date = LocalDate.parse(dateTest, DateTimeFormatter.ofPattern("yyyy-MM-dd"));		
			setValue(date);
		}
}
@PostMapping("/join")
	public void user_join_post(@ModelAttribute @Valid UserDto userDto, BindingResult bindingResult, Model model) {
		log.info("POST /user/join..."+ userDto);
		if(bindingResult.hasErrors()) {
			for(FieldError error : bindingResult.getFieldErrors()) {
				model.addAttribute(error.getField(), error.getDefaultMessage());
      }
   }
}
@InitBinder를 통해 이 컨트롤러의 WebDataBinder를 초기화한다.
@Valid를 통해 UserDto에 설정된 Annotation에 맞게 유효성검사를 실시한다.
BindingResult에 바인딩,유효성검사의 결과를 저장한다.
```

<br>

**Validation Annotation 정리** <br>
1. 숫자 유효성 검사
   - @Min(value, message) : 숫자가 주어진 최솟값보다 큰지 확인한다.
   - @Max(value, message) : 숫자가 주어진 최솟값보다 큰지 확인한다.
   - @Positive : 숫자가 양수인지 확인합니다.
   - @PositiveOrZero : 숫자가 양수 또는 0인지 확인한다.
   - @Negative : 숫자가 음수인지 확인합니다.
   - @NegativeOrZero : 숫자가 음수 또는 0인지 확인한다.
3. 문자열 유효성 검사
   - @NotBlank(message) : 문자열이 비어 있지 않은지 확인한다.
   - @Size(min, max, message) : 문자열의 길이가 주어진 범위 내에 있는지 확인한다.
   - @Email(message) : 문자열이 유효한 이메일 주소인지 확인한다.
   - @Pattern(regexp, message) : 정규 표현식에 맞는지 확인한다.
   - @URL(message) : 문자열이 유효한 URL인지 확인한다.
5. 날짜와 시간 유효성 검사
   - @DateTimeFormat(pattern) : 날짜와 시간의 형식을 지정한다.
   - @Future : 날짜가 미래인지 확인한다
   - @FutureOrPresent : 날짜가 미래이거나 현재인지 확인한다.
   - @Past : 날짜가 과거인지 확인한다.
   - @PastOrPresent : 날짜가 과거이거나 현재인지 확인한다.
7. 기타
   - @AssertTrue : Boolean타입의 값이 true인지 확인한다.
   - @AssertFalse : Boolean타입의 값이 false인지 확인한다.
   - @CreditCardNuber : 신용카드 번호의 유효성을 검증한다.

## Exception
@ExceptionHandler : 특정 컨트롤러 내에서 예외 처리를 담당한다. 예외가 발생했을 때 특정한 메서드가 호출되어 예외를 처리하고 적절한 응답을 한다.
```
@ExceptionHandler(FileNotFoundException.class)
public String fileNotFoundExceptionHandler(Exception e, Model model) {
	log.error("error : " + e);
	model.addAttribute("ex",e);
	return "exTest/error";
}

@ExceptionHandler(ArithmeticException.class)
public String arithmeticException(Exception e, Model model) {
	log.error("error : " + e);
	model.addAttribute("ex",e);
	return "exTest/error";
}
	
@ExceptionHandler(Exception.class)
public String AllExceptionHandler(Exception e, Model model) {
	log.error("error : " + e);
	model.addAttribute("ex",e);
	return "exTest/error";
}
각 Error 클래스에 따라 어떻게 처리할 것인지를 메서드로 정의해두었다.
```

<br>

@ControllerAdvice
여러 컨트롤러 클래스에서 발생하는 예외를 한 곳에서 처리할 수 있도록 도와주는 스프링 프레임워크의 기능이다.<br>
@ExceptionHandler(받아낼 예외의 종류) : 해당 annotation으로 발생하는 예외의 종류에 따라 원하는 방식으로 처리가 가능하다.
```
@ControllerAdvice
@Slf4j
public class GlobalExceptionHandler {
	
	@ExceptionHandler(NoHandlerFoundException.class)
	public String NoHandlerFoundExceptionHandler(Exception e, Model model) {
		log.error("NoHandlerFoundExceptionHandler : " + e);
		model.addAttribute("ex",e);
		return "globalError";
	}
	
	@ExceptionHandler(Exception.class)
	public String AllExceptionHandler(Exception e, Model model) {
		log.error("error : " + e);
		model.addAttribute("ex",e);
		return "globalError";
	}
}
```

<br>

## DataSource
```
@Configuration
public class DataSourceConfig {	

	@Bean
	public HikariDataSource dataSource3()
	{
		HikariDataSource dataSource = new HikariDataSource();
		// 이 객체는 DB와의 연결을 관리하는 Connection Pool역할을 한다.
		dataSource.setDriverClassName("com.mysql.cj.jdbc.Driver");
		// MySQL DB에 연결하기 위한 JDBC 드라이버 클래스명을 설정한다.
		dataSource.setJdbcUrl("jdbc:mysql://localhost:3306/bookdb");
		// DB에 연결하기 위한 JDBC URL을 설정한다. bookdb라는 이름의 DB를 사용하였다.
		dataSource.setUsername("root");
		// DB에 연결할 때 사용한 사용자명
		dataSource.setPassword("1234");
		// DB에 연결할 때 사용한 비밀번호
		return dataSource;
	}	
}
```
@Configuration : 해당 클래스가 Spring 설정 클래스임을 나타낸다. Spring 설정 클래스에서는 Bean 설정을 정의할 수 있다. <br>
@Bean : @Configuration클래스 내에서 사용되며 Spring Container에 객체를 등록하고 그 객체를 Spring의 다른 컴포넌트에서 사용할 수 있도록 한다. 해당 Annotation이 붙은 메서드의 반환타입이 Bean의 타입이 된다. <br>

<br>

## SQLMAPPER(MyBatis)
SQLMapper : 개발자가 작성한 SQL 실행결과를 객체에 매핑한다. 객체와 테이블간의 관계를 매핑하는 것이 아니라, SQL문을 직접 작성하고 쿼리의 수행결과를 객체에 매핑하는 방식이다.<br>

```
// 설정파일
@Configuration
public class MybatisConfig {
	@Autowired
	private DataSource dataSource;

	@Bean 
	public SqlSessionFactory sqlSessionFactory() throws Exception {
		SqlSessionFactoryBean sessionFactory = new SqlSessionFactoryBean();
		// SqlSessionFactoryBean 객체 생성
		sessionFactory.setDataSource(dataSource);
		// SqlSessionFactoryBean의 Datasource를 이전의 HikariDatasource로 설정한다.
		return sessionFactory.getObject();
		// SqlSessionFactory객체를 생성하고 반환한다.
	}
}
// 매핑파일
@Mapper
public interface MemoMapper {
	@SelectKey(statement="select max(id)+1 from tbl_memo",keyProperty = "id",before = false, resultType = int.class)
	// @SelectKey : 자동으로 키 값을 생성할 때 사용한다. statement는 키를 생성하기 위한 SQL쿼리를 지정한다.
	// keyProperty는 쿼리 결과를 id라는 속성에 설정하겠다는 의미. before은 @SelectKey가 실행되는 시점을 Insert실행전(true),실행후(false)로 지정한다.
	// 쿼리 결과가 반환할 데이터 타입을 지정한다.

	@Insert("insert into tbl_memo values(#{id},#{text})")
	public int insert(MemoDto dto);
	
	
	@Update("update tbl_memo set text=#{text} where id=#{id}")
	public int update(MemoDto dto);
	
	@Delete("delete from tbl_memo where id=#{id}")
	public int delete(int id);
	
	@Select("select * from tbl_memo where id=#{id}")
	public MemoDto selectAt(int id);
}
```

## Transaction
DB의 상태를 변경시키는 작업의 단위 <br>
<br>
**ACID** <br>
Atomicity(원자성) : 트랜잭션이 DB에 모두 반영되거나, 또는 전혀 반영되지 않아야 한다. <br.
Consitenty(일관성) : 트랜잭션의 작업 처리 결과는 항상 일관성 있어야한다. ex) 송금시 금액의 데이터 타입을 정수형에서 문자열로 변경할 수 없다. <br>
Isolation(독립성) : 둘 이상의 트랜잭션이 동시에 병행 실행되고 있을 때, 어떤 트랜잭션도 다른 트랜잭션 연산에 끼어들 수 없다. <br>
Durability(지속성) : 트랜잭션이 성공적으로 완료되었으면, 결과는 영구적으로 반영되어야 한다. <br>

<br>

**Transaction 연산** <br>
1. Commit : 트랜잭션이 성공적으로 수행되었음을 선언하는 연산, 결과를 최종 DB에 반영한다.
2. Rollback : 트랜잭션 수행이 실패했음을 선언하고 작업을 취소하는 연산으로, 트랜잭션이 수행되는 도중 일부 연산이 처리되지 못한 상황에 사용한다. DB를 트랜잭션 수행전과 동일한 상태로 되돌려야 한다.

<br>

**Transaction Option** <br>
1. propagation
2. isolation
3. timeout
4. readOnly
5. rollbackFor / noRollbackFor : 롤백을 수행할 예외 클래스를 지정한다. / 롤백을 수행하지 않을 예외 클래스를 지정한다.

```
@Transactional(rollbackFor = SQLException.class)
public boolean memoAddTx(MemoDto memoDto) throws SQLException {
	log.info("memoDto insert 전 " + memoDto);
	int result = memoDaoImpl.insertTx(memoDto);
	log.info("memoDto insert 후 " + memoDto);
	result = memoDaoImpl.insertTx(memoDto);
		
	return result>0;
}
// Transactional annotation에 rollbackFor옵션을 사용하여 해당 메서드에서 SQLException가 발생할 시 롤백을 수행하도록 설정하였다.
```

<br>

## RESTController
REST : REpresentative State Transfer의 약자로 분산 시스템을 위한 아키텍쳐 <br>
네트워크를 경유해서 외부 서버에 접속하거나 필요한 정보를 불러오기 위한 구조. 해당 개념을 바탕으로 설계된 시스템을 RESTFul이라고 표현한다. <br>
웹에서 화면 전환없이 이루어지는 동작은 대부분 비동기 통신을 통해 이루어지고 비동기 통신을 하기 위해서는 클라이언트가 서버로 요청메시지의 본문(body)에 데이터를 담아서 보내야한다. 서버도 클라이언트에 응답하기 위해 응답 메시지의 본문(body)에 데이터를 담아서 보내야 한다.<br>
이 때의 body를 각각 Request Body와 Response Body로 부르는데 이러한 Body에 담기는 데이터 형식은 JSON,XML등과 같은 데이터로 처리한다. <br>

@RequestBody : JSON -> VO(자바객체)로 변환해주는 Annotation <br>
@ResponseBody : VO -> JSON로 변환해주는 Annotation <br>

```
public class MemoRestController {	
	@Autowired
	private MemoServiceImpl memoServiceImpl;

	@PostMapping(value="/add_post", consumes=MediaType.APPLICATION_JSON_UTF8_VALUE)
	public void add_post(@RequestBody MemoDto memoDto) throws SQLException {
		memoServiceImpl.memoAddTx(memoDto);
	}
// consumes : 서버측이 받을 데이터 타입을 설정한다. 이 메서드에서는 JSON형식으로 데이터를 받을 것이다.
// @RequestBody를 통해 JSON으로 받은 데이터를 자바 객체로 변환하여 MemoDto클래스로 받았다.

	@GetMapping(value="/getMemo", produces=MediaType.APPLICATION_JSON_VALUE)
	public ResponseEntity<MemoDto> getMemo() {
		List<MemoDto> list = memoServiceImpl.getMemos();
		for(MemoDto dto : list) {
			System.out.println(dto);
		}
		return new ResponseEntity(memoServiceImpl.getMemos(),HttpStatus.OK);
	}
// produces : 클라이언트 측이 받을 데이터 타입을 설정한다. 이 메서드에서는 JSON형식으로 데이터를 보낼 것이다.
// ResponseEntity : 응답의 상태코드와 Body를 함께 관리한다.
}
```

<br>
View차원에서는 axios를 사용하여 get/post/put/patch/delete등의 http요청을 보낼 수 있다. <br>
각 요청에 따라 들어가는 파라미터가 다르고, Controller에서 정한 데이터타입에 따라서 View에서 데이터타입에 맞게 데이터를 전송한다. <br>

```
<!-- axios cdn-->
<script src="https://cdnjs.cloudflare.com/ajax/libs/axios/1.6.8/axios.min.js" integrity="sha512-PJa3oQSLWRB7wHZ7GQ/g+qyv6r4mbuhmiDb8BjSFZ8NZ2a42oTtAq5n0ucWAwcQDlikAtkub+tPVCw4np27WCg==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
<script>
			
		const projectPath='${pageContext.request.contextPath}';
		
		//GET

		const axiosAsyncGetBtn = document.querySelector('.axiosAsyncGetBtn');
		axiosAsyncGetBtn.addEventListener('click',function(){
			const axiosAsyncGetForm = document.axiosAsyncGetForm;
			
			axios.get(projectPath+"/memo/add_rest_get?id="+axiosAsyncGetForm.id.value+"&text="+axiosAsyncGetForm.text.value)
			.then(resp=>{console.log(resp);})
			.catch(err=>{console.log(err);});	
		})
	
		//POST

		const axiosAsyncPostBtn = document.querySelector('.axiosAsyncPostBtn');
		axiosAsyncPostBtn.addEventListener('click',function(){
			//form
			const axiosAsyncPostForm = document.axiosAsyncPostForm;
			
			//header x
			const headers = {'Content-Type' : 'application/json'};
			//param
			const param = {
					"id" : axiosAsyncPostForm.id.value,
					"text" : axiosAsyncPostForm.text.value		
			}
			
			//요청
			axios.post(projectPath+"/memo/add_rest_post",param,headers)
			.then(resp=>{console.log(resp);})
			.catch(err=>{console.log(err);});	
		})	
</script>

```

## AOP
AOP는 Aspect Oriented Programming의 약자로 관점 지향 프로그래밍이라고 불린다. <br>
관점 지향은 어떤 로직을 기준으로 핵심적인 관점, 부가적인 관점으로 나누어서 보고 그 관점을 기준으로 각각 모듈화하겠다는 것이다. <br>
여기서 모듈화란 어떤 공통된 로직이나 기능을 하나의 단위로 묶는 것을 말한다. <br>
 
소스 코드상에서 다른 부분에 계속 반복해서 쓰는 코드들을 발견할 수 있는 데 이것을 흩어진 관심사 (Crosscutting Concerns)라 부른다. <br>

**AOP 주요 개념** <br>
Aspect : 흩어진 관심사를 모듈화 한 것. 주로 부가기능을 모듈화한다.
Target : Aspect를 적용하는 곳 (클래스, 메서드 등.. )
Advice : 실질적인 부가기능을 담은 구현체
JointPoint : Advice가 적용될 위치, 끼어들 수 있는 지점을 의미한다. Advice는 메서드 진입 지점, 생성자 호출 시점, 필드에서 값을 꺼내올 때 등 다양한 시점에 적용가능하다.
PointCut : JointPoint의 상세한 스펙을 정의한 것으로 '~ 메서드의 진입 시점에 호출할 것'과 같이 더욱 구체적으로 Advice가 실행될 지점
을 정할 수 있다.
<br>

**AOP Annotion** <br>
@Before : Advice target 메소드가 호출되기 전에 어드바이스 기능을 수행한다.
@After  : target 메소드의 결과에 관계없이(성공, 예외 관계없이) 타겟 메소드가 완료 되면 어드바이스 기능을 수행
@AfterReturning : 타겟 메소드가 성공적으로 결과값을 반환 후에 어드바이스 기능을 수행
@AfterThrowing : 타겟 메소드가 수행 중 예외를 던지게 되면 어드바이스 기능을 수행
@Around : 어드바이스가 타겟 메소드를 감싸서 타겟 메소드 호출전과 후에 어드바이스 기능을 수행

