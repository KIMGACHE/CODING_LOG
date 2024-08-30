## JavaScript

### JavaScript의 기본 자료형
1. Number : 실수와 정수를 모두 Number로 취급한다.
2. String : 문자열
3. Object : {Key:Value}의 쌍으로 데이터가 저장된다.
4. null : null은 object 자료형을 사용하며 빈 값을 의미한다. -> 공간을 차지하고 있다는 의미이다.
5. undefined : 이름은 부여했으나 (선언) 정의는 하지않은 상태를 의미한다. -> 공간을 차지하지 않는다.
6. boolean : true,false의 두 가지 값을 가지고, 옳고 그름을 판단한다.

typeof 뒤에 데이터를 놓으면 해당 데이터의 타입을 알 수 있다.
```
document.write(typeof 10); -> Number
document.write(typeof 10.5); -> Number
document.write(typeof "HELLO WORLD"); -> String
document.write(typeof {name:"홍길동", age:55, gender:"M"}); -> Object

let val = null;
document.write(typeof val); -> Object

let val2;
document.write(typeof val2); -> undefined

document.write(typeof 10<5); -> true
```
