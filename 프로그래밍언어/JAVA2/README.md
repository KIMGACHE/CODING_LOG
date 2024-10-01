## JAVA

### 기본 API 클래스
최상위 클래스 Object <br>
- 모든 클래스의 최상위의 부모 클래스
- extends 키워드로 다른 클래스를 상속하지 않으면 암시적으로 java.lang.Object 클래스를 상속
- 자바의 모든 클래스는 Object 클래스의 자식이거나, 자손클래스
<br>

**toString()** <br>
- 객체가 가지고 있는 정보나 값들을 문자열로 만들어 리턴하는 메서드
- 일반적으로 그 객체를 설명해주는 문자열을 리턴
<br>

**equals()** <br>
- 두 객체가 동일 객체인지 동등비교시 사용
- 동일시 true, 동일하지 않을 때 false를 반환
<br>

**hashCode()** <br>
- hashcode : 객체를 식별하는 하나의 정수값
- hashCode() : JVM이 객체를 식별하기 위해 부여한 정수형태의 위치값을 반환하는 함수, 객체의 메모리 번지를 이용해서 해시코드를 만들고 리턴한다.
<br>

**Wrapper 클래스** <br>
자바의 기본 자료형(원시타입)을 객체 타입으로 처리할 수 있도록 만든 클래스이다.<br>
```
// Boxing (기본자료형 -> Wrapper Class)
Integer ob1 = new Integer(100);
Integer ob2 = new Integer("200");
Integer ob3 = Integer.valueOf("300");

// UnBoxing ( Wrapper Class -> 기본자료형)
int n1 = ob1.intValue();
```
<br>

**Date** <br>
```
Calendar cal = Calendar.getInstance(); // 캘린더는 싱클톤 패턴이다.
System.out.println(cal);
System.out.println(cal.get(Calendar.YEAR)); // 년도
System.out.println(cal.get(Calendar.MONTH)+1); // 월, 0부터 세기때문에 +1을 해준다.
System.out.println(cal.get(Calendar.DAY_OF_MONTH)); // 일, 이번달의 몇일인지
System.out.println(cal.get(Calendar.DAY_OF_WEEK)); // 요일(1-7, 일-토)
System.out.println(cal.get(Calendar.HOUR_OF_DAY)); // 시간
System.out.println(cal.get(Calendar.MINUTE)); // 분
System.out.println(cal.get(Calendar.SECOND)); // 초
```
<br>

### 예외처리
**오류의 종류** <br>
1. 컴파일 에러(compile error) - 컴파일할 때 발생하는 에러
2. 실행 오류(runtime error) - 실행할 때 발생하는 에러(가장 치명적)
   - 시스템오류
   - 예외(프로그램이 실행되는 동안에 발생하는 예기치 않은 에러)
4. 내가 원하는대로 작동하지 않는 경우, bug

<br>

**try-catch구문** : 예외처리<br>
```
String str = null;
try {
   System.out.println(str); // 예외가 발생할 것같은 코드를 try에 적어주고 예외가 발생하면 예외 객체가 만들어진다.
} catch(NullPointerException e) { // try에 있는 코드에 의해 생성된 예외 객체를 받는다.
   e.printStackTrace();
}
```
<br>

**Throw & Throws** <br>
예외의 방향, 처리를 직접한다. 예외가 발생한 코드에서 try-catch구문을 사용하는 것이 아니라 예외 객체를 코드를 실행하는 위치로 던진다. <br>
throws : 예외가 발생하면 상위메서드로 예외를 던진다. <br>
thorw : 예외를 강제로 발생시킨 후 상위 블럭이나 catch문으로 예외를 던진다. <br>

### Generic 자료형
자료형을 객체가 생성되는 시점에 정하는 문법 <br>
클래스 내부에서 사용할 데이터 타입을 외부에서 지정하는 기법 <br>
```
class 호빵 <T> {
   private T material;
   호빵(T material) {
      this.material = material;
   }
}
class 팥 {
   public String toString() {
      return "팥";
   }
}

public static void main(String[] args) {
   호빵<팥> ob1 = new 호빵<팥>(new 팥());
}
```
<br>
Generic 타입으로 사용할 자료형을 제한하고 싶다면 사용할 자료형에 상위 클래스를 만들어 상속시킨다. <br>
예를 들어, 호빵을 <T extends 재료> 로 정의하고 팥이 재료 클래스를 상속받게끔 하면 재료를 상속하는 클래스만이 호빵에 T로 들어갈 수 있다. <br>
복수개의 Generic이 필요하다면 <>연산자 안에 복수개의 Generic 타입을 시정한다. <br.
메서드의 리턴타입으로도 Generic 타입(<>)을 사용할 수 있다.






