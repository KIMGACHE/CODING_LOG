## JavaScript

### JavaScript의 기본 자료형
1. **Number** : 실수와 정수를 모두 Number로 취급한다.
2. **String** : 문자열
3. **Object** : {Key:Value}의 쌍으로 데이터가 저장된다.
4. **null** : null은 object 자료형을 사용하며 빈 값을 의미한다. -> 공간을 차지하고 있다는 의미이다.
5. **undefined** : 이름은 부여했으나 (선언) 정의는 하지않은 상태를 의미한다. -> 공간을 차지하지 않는다.
6. **boolean** : true,false의 두 가지 값을 가지고, 옳고 그름을 판단한다.

**typeof** 뒤에 데이터를 놓으면 해당 데이터의 타입을 알 수 있다.
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

**변수 선언과 정의** <br>
let, const를 통해 공간에 이름을 부여할 수 있다. <br>
공간 = 값; 이라는 코드가 있을 때 오른쪽을 먼저 처리한다. <br>
즉, 데이터를 먼저 저장하고 그 뒤에 이름을 붙인다는 의미이다. <br>

<br>

let : 변수 선언 예약어 <br>
const : 심볼릭 상수 선언 예약어 (문자형 형태로 상수를 만들 때 사용된다.) <br>

### String
```
let str1 = "hello";
let str2 = 'world';
console.log(str1 + str2); -> +로 문자열과 문자열을 잇게되면 서로 연결된다 helloworld

str1 = "abcd" -> let으로 정의된 변수는 값을 변경할 수 있다.
const str3 = "Const Value";
str3 = "abcd" -> const로 정의된 상수는 값을 변경하려고 하면 오류가 발생한다.
```
<br>

**보간법** : 변수,함수 호출 및 산술 표현식을 문자열에 삽입할 수 있는 기능 <br>
${value} 형식을 사용, 백틱(``)에만 사용가능하다.
```
let tmp = "VALUE";
console.log(`TEST : ${1+2+3}`); -> 1+2+3이라는 문자열이 출력되는 것이 아니라 연산되어 6이 출력된다.
console.log(`TEST : ${tmp}`); -> tmp라는 변수를 출력한다.
```

### Object
Key와 Value가 한 쌍을 이루면서 데이터를 저장하는 자료형. <br>
속성(field)와 기능(function)으로 이루어진다. <br>
```
const poppi = {
            //속성(field)
            name:"뽀삐",
            kind:"포메라니안",
            age:1,
            //기능(함수)
            sound: ()=>{
                alert(poppi.name+"이 소리를 냅니다.");
            },
            toString: ()=> {
                alert(
                    "이름 : " + poppi.name + "\n나이 : " + poppi.age + "\n견종 : " + poppi.kind 
                )
            }
        };
```

### Object Array
배열 : 동일한 자료형의 데이터를 저장할 때 사용한다. <br>
자바와 자바스크립트는 배열에 자료형의 종류가 동일하지 않더라도 저장할 수 있게끔 되었다.

```
const arr2 = ['str1', 'str2', null, true, 30, {name:"홍길동", age:55},false,undefined, {name: '남길동', age:46}];
```





















