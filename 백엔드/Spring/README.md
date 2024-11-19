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

