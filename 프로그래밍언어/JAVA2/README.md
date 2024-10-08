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
**Reader클래스의 주요 메서드** <br>
- int read() : 단일 문자를 하나 읽어와 읽은 문자의 유니코드값을 리턴한다.
- int read(char[] b) : 문자를 b의 크기만큼 읽어 b에 저장하고, 읽은 문자 개수를 리턴한다.
- abstract int read(byte[] b, int off, int len) : len만큼 읽어 b의 off위치에 저장하고, 실제 읽어 온 문자 개수를 리턴한다.

**Writer클래스의 주요 메서드** <br>
- void write(String s) : 문자열 s를 출력한다.
- void write(char[] b) : char 배열 b를 출력한다.
- void write(char[] b, int off, int len) : b의 off위치부터 len만큼 문자를 출력한다.
- void write(String s, int off, int len) : s의 off위치부터 len만큼 문자열을 출력한다.

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

<br>

**파일 관련 클래스** <br>
- File : 경로 정보를 바탕으로 해당 파일을 사용하는 객체를 생성하고, 파일과 디렉토리 관련 여러 메서드를 제공한다.
- FileReader : 파일에서 문자 스트림을 기반으로 한 입력을 처리하는 클래스
- FileWriter : 파일에서 문자 스트림을 기반으로 한 출력을 처리하는 클래스
- FileInputStream : 파일에서 바이트 스트림을 기반으로 한 입력을 처리하는 클래스이다.
- FileOutputStream : 파일에서 바이트 스트림을 기반으로 한 출력을 처리하는 클래스이다.

**객체 단위 데이터를 전달하려면 Serializable을 implements하여 사용해야 문제없이 전달할 수 있다.** <br>
<br>

```
Reader fin = new FileReader("C:\\TMP_IO\\test.txt");
StringBuffer buffer = new StringBuffer();
int data; (단일 문자 하나를 읽어와 유니코드 값 0~65535를 리턴한다. 2byte이기때문)
while((data=fin.read())!=-1) { // Reader의 read()함수는 반환타입이 int이다. 읽을 문자열이 없다면 -1을 리턴하므로 반복문이 끝난다.
   buffer.append((char)data);
}

Writer fout = new FileWriter("C:\\TMP_IO\\test.txt",true); // 파일이 존재하지 않으면 파일을 생성한다. 기본값은 덮어쓰기고 true항목을 파라미터로 넣어주게되면 추가로 내용을 덧붙일 수 있다.
fout.write("HELLOWORLD\n");
fout.flush(); // buffer공간을 초기화
fout.close();

// -----------------------------------------------------------------------------
InputStream fin = new FileInputStream("C:\\TMP_IO\\data.xlsx);
while(true) {
   int data = fin.read(); // 1byte단위로 읽어오므로 0~255사이의 숫자를 반환한다.
   if(data==-1)
      break;
   System.out.print((char)data);
}

OutputStream fout = new FileOutputStream("C:\\TMP_IO\\test.txt");
fout.write('a');
fout.write('가'.getBytes(StandardCharsets.UTF_8)); // 문자열은 2byte?라 공백처리되므로 처리를 해야한다.
```

## JDBC 프로그래밍
JAVA와 DBMS를 연결해주는 여러가지 클래스를 사용하기 위해서는 Driver 클래스가 필요하다. (각 DBMS마다 Driver클래스가 다르다.) <br>
<br>
JDBC프로그래밍 단계
1. JDBC Driver 로드
2. 데이터베이스 연결
3. Statement(SQL문) 생성
4. Statement(SQL문) 전송
5. 결과 받기
6. 연결해제

<br>

**기본** <br>
```
String id = "root"; // DB이름
String pw = "1234"; // DB비밀번호
String url = "jdbc:mysql:/localhost:3306/testdb"; // DB경로

// JDBC 참조변수
Connection conn = null;
PreparedStatement pstmt = null;
ResultSet rs = null;

try {
   Class.forName("com.mysql.cj.jdbc.Driver");
   conn = DriverManager.getConnection(url,id,pw); // connection 객체를 만든다.
} catch(Exception e) {
   e.printStackTrace();
} finally {
   try {
      conn.close();
   } catch(SQLException e) {
      e.printStackTrace();
   }
}
```
<br>

**INSERT** <br>
```
try {
   Class.forName("com.mysql.cj.jdbc.Driver");
   conn = DriverManager.getConnection(url,id,pw); // connection 객체를 만든다.

   pstmt = conn.preparStatement("insert into tbl_std values(?,?,?)"); // 미리 Statement를 만들어두고 전송한다. 변수는 ?로 처리한다.
   pstmt.setString(1,"홍길동"); // 첫번째 파라미터에는 statement에 들어간 ?의 인덱스를 적는다.
   pstmt.setInt(2, 55); // 두번째 파라미터에는 해당 인덱스에 해당하는 값이 들어간다.
   pstmt.setString(3,"대구"); // 각 변수의 타입을 확인하여 매서드를 사용해야한다.

   int result = pstmt.executeUpdate();
   // DML(INSERT,UPDATE,DELETE)문장 실행, 문제가 발생하면 0을 return한다.
}
```

<br>

**UPDATE** <br>
```
try {
   Class.forName("com.mysql.cj.jdbc.Driver");
   conn = DriverManager.getConnection(url,id,pw); // connection 객체를 만든다.

   pstmt = conn.preparStatement("update tbl set age=? where name=?");
   pstmt.setInt(1,22);
   pstmt.setString(2,"홍길동");

   int result = pstmt.executeUpdate();
   // DML(INSERT,UPDATE,DELETE)문장 실행, 문제가 발생하면 0을 return한다.
}
```

<br>

**DELETE** <br>
```
try {
   Class.forName("com.mysql.cj.jdbc.Driver");
   conn = DriverManager.getConnection(url,id,pw); // connection 객체를 만든다.

   pstmt = conn.preparStatement("delete from tbl_std where name=? and age=? and addr=?");
   pstmt.setString(1, "홍길동");
   pstmt.setInt(2,22);
   pstmt.setString(3,"대구");

   int result = pstmt.executeUpdate();
   // DML(INSERT,UPDATE,DELETE)문장 실행, 문제가 발생하면 0을 return한다.
}
```

<br>

**SELECT** <br>
```
try {
   Class.forName("com.mysql.cj.jdbc.Driver");
   conn = DriverManager.getConnection(url,id,pw); // connection 객체를 만든다.

   pstmt = conn.preparStatement("select * from tbl_std");
   rs = pstmt.executeQuery(); // resultset에 연결

   if(rs!=null) { // rs.next()는 커서를 다음 row로 이동한다.
      while(re.next()) { // 테이블의 row를 읽으면서 데이터가 있으면 true를 반환하고 더 이상 읽을게 없으면 false를 반환한다.
         System.out.print(rs.getString(1)+" ");
         System.out.print(rs.getString(2)+" ");
         System.out.print(rs.getString(3)+" ");
         System.out.println();
      }
   }

} catch(Exception e) {
   e.printStackTrace();
} finally { // 나중에 만들어진 객체를 먼저 close해야한다.
   try {
      rs.close();
   } catch(SQLException e) {
      e.printStackTrace();
   }
   try {
      pstmt.close();
   } catch(SQLException e) {
      e.printStackTrace();
   }
   try {
      conn.close();
   } catch(SQLException e) {
      e.printStackTrace();
   }
}
```

## 디자인패턴 종류
1. 싱글톤 패턴 : 어플리케이션에서 특정 클래스의 인스턴스를 하나만 생성하도록 보장하는 패턴이다. 전역 변수를 사용하지 않고도 객체에 접근할 수 있으며, 인스턴스가 필요한 경우 항상 동일한 인스턴스를 반환합니다.
2. 팩토리 메서드 패턴 : 관련된 객체들의 집합을 생성하기위한 인터페이스를 제공하는 패턴이다. 서로 다른 구체적인 팩토리 클래스를 사용하여 다른 종류의 객체를 생성할 수 있으며, 클라이언트는 팩토리 인터페이스를 통해 객체를 생성하고 사용한다.
3. 빌더 패턴 : 복잡한 객체의 생성 과정을 추상화하여 표현하는 패턴이다. 객체의 구성 요소를 단계적으로 추가하거나 변경하여 객체를 생성할 수 있으며, 객체의 생성 과정을 사용자에게 노출 시키지 않는다.
4. 프로토 타입 패턴 : 기존 객체를 복제하여 새로운 객체를 생성하는 패턴이다. 복잡한 초기화 과정이 필요한 객체를 쉽게 생성할 수 있으며, 객체 간의 참조 문제를 피할 수 있다.
5. 어댑터 패턴 : 호환되지 않는 인터페이스를 가진 클래스들을 함께 동작하도록 만드는 패턴이다. 어댑터 클래스를 사용하여 서로 다른 인터페이스를 가진 클래스들이 함게 작동할 수 있도록 중개 역할을 수행한다.
6. 옵저버 패턴 : 한 객체의 상태 변화를 관찰하는 다른 객체들에게 자동으로 알림을 전달하는 패턴이다. 주체와 관찰자로 구성되며 상태변화가 발생하면 관찰자들에게 알림이 전달된다.
7. 전략 패턴 : 실행 중에 알고리즘을 선택할 수 있도록 하는 패턴이다. 알고리즘을 캡슐화하여 각각의 전략을 독립적으로 변경할 수 있으며, 클라이언트는 전략을 선택하여 사용한다.

## LAMDA식
람다식은 **매개변수** + **실행문**으로 구성된다. 메서드 이름과 반환타입이 모두 생략되는 구조이다. <br>
() -> {}; <br>

**작성법**
1. 메서드의 이름과 반환타입을 제거하고 '->'를 블록{} 앞에 추가한다.
   ```
   // 이전의 코드
   int max(int a, int b) { return a>b ? a: b; }

   // 람다식
   (int a, int b) -> { return a>b ? a:b; }
   ```
3. 반환값이 있는 경우 식이나 값만 적고 return문을 생략 가능하다. (;을 끝에 붙이지 않는다.)
   ```
   (int a, int b) -> a>b ? a:b
   ```
5. 매개변수의 타입이 추론 가능하면 생략 가능하다.(대부분의 경우 생략이 가능하다.)
   ```
   (a,b) -> a>b ? a:b
   ```

**주의사항**
1. 매개변수가 하나인 경우, 타입이 없는 경우에만 ()를 생략할 수 있다.
   ```
   a -> a*a
   ```
3. 블록 안의 문장이 하나뿐일 때, 괄호 {}를 생략가능 하다. (;을 끝에 붙이지 않는다.)
   ```
   (int i) -> System.out.println(i)
   ```
5. 단 하나뿐인 문장이 return문이면 괄호{} 생략불가 (return을 생략하면 생략가능하다).
   ```
   (int a, int b) -> { return a>b ? a:b; }
   ```

<br>

**람다식은 함수형 인터페이스의 미완성된 메서드를 완성시켜 사용할 수 있다.** <br>
```
// 덧셈, 뺄셈, 곱셈, 나눗셈을 수행하는 함수형 인터페이스 정의
interface Calculator {
	int calculator(int num1, int num2);
	
}

public class C03LAMDA {

	public static void main(String[] args) {
		
		Calculator add = (num1,num2)->{return num1+num2;};
		Calculator sub = (num1,num2)->num1-num2;
		Calculator mul = (num1,num2)->{return num1*num2;};
		Calculator div = (num1,num2)->{return num1/num2;};
		
		int a = 10;
		int b = 2;
		int sum = add.calculator(a, b);
		System.out.println(sum);

	}

}
```

## Stream
자바 스트림은 Collection을 처리하고 변환하기 위한 강력한 기능을 제공한다. <br>
스트림을 사용하면 데이터를 효율적으로 처리하고 다양한 연산을 수행할 수 있습니다. <br>
<br>
**중개 연산(Intermediate Operations)**: <br>
스트림의 요소를 변환하거나 필터링하는 작업을 수행한다. 파이프라인에 의해 여러번 호출 할 수 있다.<br>
중개 연산만으로는 실제로 데이터가 처리되지 않으며, 최종 연산이 호출될 때까지 연산이 지연된다. <br>
1. filter: 주어진 조건에 맞는 요소를 선택한다.
2. map: 요소를 다른 형태로 변환한다.
3. flatMap: 각 요소를 변환하고 이를 하나의 스트림으로 평면화한다.
4. distinct : 중복된 요소를 제거한다.
5. sorted: 요소를 정렬한다.
6. limit: 주어진 개수만큼 요소를 제한한다.
7. skip: 처음 몇 개의 요소를 제외하고 반환한다.
<br>
**최종 연산(Terminal Operations)**: <br>
1. forEach: 각 요소를 반복적으로 처리한다.
2. collect: 요소를 수집하여 새로운 컬렉션을 생성한다.
3. reduce: 요소를 하나로 줄여서 결과를 반환한다.
4. min/max: 최소/최대값을 반환한다.
5. count: 요소의 개수를 반환한다.
 
```
List<Integer> list = Arrays.asList(1,2,3,4,5);

List<Integer> list2 = list.stream() // List를 Stream으로 변환한다.
			.filter(n->n%2==1) // 홀수인 요소만을 선택한다.
			.map(n->n*n) // 요소를 제곱한 값으로 변경한다.
			.collection(Collectors.toList()); // Stream을 List로 변환한다.

List<Person> list3 = Arrays.asList(
	new Person("박효신추억은사랑을닮아",40),
	new Person("김범수끝사랑",45),
	new Person("자이언티",30)
	);

List<Person> list4 = list3.stream() // List를 Stream으로 변환한다.
			.map(Person::getAge) // 요소를 Person클래스의 getAge의 반환값으로 변환한다.
			.sorted((a,b)->{return b-a;}) // Stream을 내림차순으로 정렬한다.
			.collect(Collectors.toList()); // Stream을 List로 변환한다.
```

## 함수형 프로그래밍
함수형 인터페이스를 사용할거면 인터페이스에 추상 메서드를 하나만 만든다. <br>
그리고 @FunctionalInterface를 붙여줌으로써 컴파일러가 해당 interface가 함수형인지 알 수 있다.<br>

```
@FunctionalInterface
interface Func1 { void say(String message); }
@FunctionalInterface
interface Func2 { int sum(Integer ...args); }
@FunctionalInterface
interface Func3 { List<Integer> createListDesc(int ...args); }

public static void main(String[] args) {
   Func1 func1 = (message) -> {System.out.println(message);}; // 추상 메서드를 변수 선언과 동시에 완성시킨다.
   func1.say("HelloWorld");

   Func2 func2 = (arg) -> {
      int sum = 0;
      for(int el:arg) {
         sum+el;
      }
      return sum;
   }
   System.out.println(func2.sum(1,2,3,4,5,6,7,8,11,22,66));
   Func3 func3 = (arg)->{
      return Arrays.stream(arg)
			.boxed()	// sorted가 원시타입 int를 지원하지않아 Integer로 매핑
			.sorted((a,b)->{return b-a;})
			.collect(Collectors.toList());
   };
   List<Integer> li = func3.createListDesc(6,55,4,22,88,999,1,23,333,3125);
   System.out.println(li);
}
```
**제공되는 함수형 인터페이스** <br>
1. Function<T, R> : apply 메서드를 가지고 있어서 하나의 인자(T)를 받아 결과(R)을 반환하는 함수형 인터페이스이다.
2. Supplier<T> : get 메서드를 가지고 있어서 어떠한 인자도 받지 않고 결과만을 제공하는 함수형 인터페이스이다.
3. Consumenr<T> : accept 메서드를 가지고 있어서 어떠한 인자를 받아서 결과를 반환하지 않는 함수형 인터페이스이다.
4. Predicate<T> : test 메서드를 가지고 있어서 어떠한 인자를 받아서 Boolean타입의 결과를 반환하는 함수형 인터페이스이다.
5. UnaryOperator<T> : apply 메서드를 가지고 있어서 하나의 인자를 받아서 동일한 타입의 결과를 반환하는 함수형 인터페이스이다.
6. BinaryOperator<T> : apply 메서드를 가지고 있어서 두 개의 인자를 받아 동일한 타입의 결과를 반환하는 함수형 인터페이스이다.

## Class Diagram
클래스 다이어그램은 클래스 간의 관계를 도식화한 것으로 UML의 한 종류이다. <br>
![image](https://github.com/user-attachments/assets/dda76cbc-4a44-481c-9d6c-4d9368bfa370)
<br>
- 일반화, 실체화의 경우 상속관계를 의미하고 추상클래스나 인터페이스일 경우 점선으로 그 이외에는 실선으로 표시한다.
- 의존의 경우 클래스 내부의 멤버함수가 또 다른 클래스의 객체를 파라미터로 받는 경우에 사용한다.
- 연관의 경우 클래스 내부의 멤버변수가 다른 클래스 자료형을 가지는 경우에 사용한다.
- 집합과 합성의 경우 한 클래스 내부에 다른 클래스의 객체를 생성하여 사용하는 경우에 사용하는데 집합의 경우에 해당 객체가 의존적이지 않으나 합성의 경우 의존적이다(?)


