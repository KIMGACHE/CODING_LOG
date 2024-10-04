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

## 컬렉션 프레임워크
널리 알려진 자료구조를 사용해서 객체를 효율적으로 추가,삭제,검색할 수 있도록 미리 구현된 인터페이스와 클래스 
컬렉션 : 객체의 저장 <br>
프레임워크 : 사용 방법을 정해놓은 라이브러리 <br>

### List 컬렉션
자료를 일렬로 나열하여 저장하는 방식, 배열과 유사하나 데이터 저장시 필요한 만큼의 공간이 자동으로 증가한다.<br>
객체 자체를 저장하는 것이 아니라 객체가 존재하는 주소 번지를 저장 <br>

1. ArrayList : **List<E> 리스트이름 = new ArrayList<E>();** (E는 타입파라미터)
2. Vector : **List<E> 리스트이름 = new Vector<E>();**
   - ArrayList와 다르게 멀티 스레드 환경에서 안전하게 객체를 추가/삭제할 수 있다.
4. LinkedList : **List<E> 리스트이름 = new LinkedList<E>();**
   - 내부 배열 형태가 아닌 인접 참조를 링크해서 체인처럼 관리, 기존의 ArrayList에 비해서 데이터 추가/삭제시 성능향상

### List의 공통메서드
1. 객체 추가
   - boolean add(E e) : 주어진 객체를 맨 끝에 추가한다.
   - void add(int index, E e) : 주어진 인덱스에 객체를 추가
   - E set(int index, E e) : 주어진 인덱스에 저장된 객체를 주어진 객체로 변경
3. 객체 검색
   - boolean contains(Object o) : 주어진 객체가 저장되어있는지 조사
   - E get(int index) : 주어진 인덱스에 저장된 객체를 리턴
   - boolean isEmpty() : 컬렉션이 비어있는지 조사
   - int size() : 저장되어있는 전체 객체 수를 리턴
5. 객체 삭제
   - void clear() : 저장된 모든 객체를 삭제
   - E remove(int index) : 주어진 인덱스에 저장된 객체를 삭제
   - boolean remove(Object o) : 주어진 객체를 삭제

### Set 컬렉션
저장 순서가 유지되지 않는 형태의 저장방식, 수학의 집합과 유사하다. <br>
순서와 상관없고 중복이 허용되지 않는다. <br>

1. Hashset : **Set <E> set이름 = new HashSet<E>();**
   - 순서 없이 저장, 동일 객체는 중복 저장하지 않는다.
   - hashCode() 메서드를 호출해서 얻어낸 해시코드를 통해 객체의 동등비교후 중복되지않는 데이터 set
3. LinkedHashSet
4. TreeSet

### Set의 공통메서드
1. 객체 추가
   - boolean add(E e) : 주어진 객체를 저장한다. 중복 객체면 false를 리턴하고 성공적으로 저장되면 true를 리턴한다.
3. 객체 검색
   - boolean contains(Object o) : 주어진 객체가 저장되어 있는지 조사
   - boolean isEmpty() : 컬렉션이 비어있는지 조사
   - Iterator<E> iterator() : 저장된 객체를 한번씩 가져오는 반복자를 리턴
   - int size() : 저장되어 있는 전체 객체 수를 리턴
5. 객체 삭제
   - void clear() : 저장된 모든 객체를 삭제
   - boolean remove(Object o) : 주어진 객체를 삭제

```
Iterator<String> iter = set.iterator();
while(iter.hasNext()) {
   System.out.println(iter.next());
}
```
### Map 컬렉션
키와 값으로 구성되며, 키는 중복저장될 수 없지만 값은 중복저장이 가능하다. <br>
기존의 저장된 키와 동일한 키로 값을 저장하면 기존의 값은 없어지고 새로운 값으로 대체된다. <br>

1. HashMap : **Map<k,v> map이름 = new HashMap<k,v>();** (k-key타입, v-value타입)
   - Map 인터페이스를 구현한 대표적인 Map 컬렉션
   - HashMap의 키로 사용할 객체는 hashCode()와 equals()메서드를 재정의 해서 동등객체가 될 조건을 정해야 한다.
3. Hashtable : **Map<k,v> map이름 = new Hashtable<k,v>();**
   - HashMap과 동일한 내부구조를 가지고 있다. 차이점은 동기화된 메서드 구성으로 인해 스레드 환경으로부터 안전하다는 것이다.
5. LinkedHashMap
6. Properties
7. TreeMap

### Map의 공통메서드
1. 객체 추가
   - V put(K key,V value) : 주어진 키로 값을 저장하고 새로운 키일 경우 null을 리턴한다. 동일한 키가 존재할 경우 값을 대체하고 이전 값을 리턴한다.
3. 객체 검색
   - boolean containsKey(Object key) : 주어진 키가 있는지 여부를 확인한다.
   - boolean containsValue(Object value) : 주어진 값이 있는지 여부를 확인한다.
   - Set<Map.Entry<K,V>> entrySet() : 키와 값의 쌍으로 구성된 모든 Map.Entry객체를 set에 담아서 리턴한다.
   - V get(Object key) : 주어진 키에 대응되는 값을 리턴한다.
   - boolean isEmpty() : 컬렉션이 비어있는지 여부를 확인한다.
   - Set<K> keySet() : 모든 키를 Set객체에 담아서 리턴한다.
   - int size() : 저장된 키의 총 수를 리턴한다.
   - collection<> values() : 저장된 모든 값을 collection에 담아서 리턴한다.
5. 객체 삭제
   - void clear() : 모든 Map.Entry(키와 값)을 삭제한다.
   - V remove(Object key) : 주어진 키와 일치하는 Map.Entry를 삭제하고 값을 리턴한다.

## GUI - Swing
```
JFrame frame = new JFrame("Title");
frame.setBounds(x좌표,y좌표,가로길이,세로길이);
frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); // 기본 종료 버튼 생성
frame.setVisible(true); // 화면상에 frame생성

class C02GUI extends JFrame {
   C02GUI() {
      super("두번째 프레임입니다.");
      setBounds(100,100,500,500);
   }
}
```
## 자바 입출력
I/O(Input/Output), 자바에서는 java.io패키지로 다양한 입출력 기능을 제공한다.<br>
**키보드,파일** => (입력스트림) => 프로그램 => (출력스트림) => **모니터,파일,프린터** <br>
<br>
스트림(Stream)은 입출력 장치와 프로그램 간 데이터 전송 통로를 말한다.<br>
단방향 통신을 제공하기 때문에 입력과 출력을 처리하려면 두개의 스트림이 필요하다.<br>
스트림은 크게 문자 스트림과 바이트 스트림으로 구분된다. <br>
<br>
1. 문자스트림
   - Reader
   - Writer
3. 바이트스트림
   - InputStream
   - OutputStream
<br>
**InputStream클래스의 주요 메서드** <br>
- int read() : 추상 메서드로 입력스트림에서 한 바이트씩 읽어서 0~255사이의 값 리턴, 끝에 도달하여 읽을 수 없을 때 -1 리턴
- int read(byte[] b) : b의 크기만큼 읽어와 b에 저장하고, 읽어 온 바이트 개수를 리턴한다. 끝에 도달하면 -1 리턴
- int read(byte[] b, int off, int len) : 최대 len만큼 읽어 b의 off위치에 저장하고, 읽은 바이트 개수를 리턴. 끝에 도달하면 -1 리턴
- int available() : 읽을 수 있는 바이트 개수를 리턴한다.
- void close() : 입력 스트림을 닫아 스트림과 관련된 시스템 자원을 반환한다.

**OutputStream클래스의 주요 메서드** <br>
- int write(int b) : b의 하위 8비트를 출력한다.
- int write(byte[] b) : b의 내용을 출력한다.
- int write(byte[] b, int off, int len) : b의 off위치부터 len만큼 바이트를 출력한다.
- int flush() : 버퍼에 남은 바이트를 출력한다.
- void close() : 출력 스트림을 닫아 스트림과 관련된 시스템 자원을 반환한다.

