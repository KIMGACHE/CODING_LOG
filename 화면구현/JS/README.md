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
배열의 요소에 접근하려면 index를 사용한다.

```
const arr2 = ['str1', 'str2', null, true, 30, {name:"홍길동", age:55},false,undefined, {name: '남길동', age:46}];
console.log(arr2[0]);
console.log(arr2[1]);
console.log(arr2[2]);
```

<br>

**PUSH/POP : JS배열을 동적 확장이 가능하다.** <br>
```
let arr = [1,2,3];
arr[5] = 100;
// 현재 배열에서는 arr[2]까지밖에 없으나 arr의 5 index위치에 100을 저장하고 그 사이의 index에는 undefined가 생긴다.

arr.push(10);
arr.push(20);
// push함수를 통해 배열의 마지막에 요소를 추가할 수 있다.
arr.pop();
arr.pop();
// pop함수를 통해 배열의 마지막에 요소를 제거할 수 있다.
```

<br>

**배열의 내용을 반복 순회하는 방법** <br>
```
1. for(초기값;조건식;탈출연산식){}
for(i=0;i<arr.length;i++){console.log(arr[i];}

2. for( 인덱스 in 배열) {}
for( i in arr) { console.log(arr[i]);}

3. forEach( ()=>{} ) // 매우 중요
arr.forEach((item)=>{console.log(item)});
// 여기서 item은 인덱스가 아니라 요소 하나하나의 값을 가져오는 것이다.
// Object에는 forEach가 먹히지 않는다.
```

<br>

**배열 정렬 함수 sort** <br>
```
arr.sort(); // 기본값으로 배열을 오름차순 정렬한다.
arr.sort((a,b)=>{return b-a}); // 배열을 내림차순 정렬한다.
```

<br>

**배열관련 함수 filter (매우 중요)** <br>
```
arr.filter( (배열요소)=> {어떤 요소를 걸러낼건지에 대한 조건식} )

let arr4 = [10,15.2, 't1', 't2', 30, true, null, 100, {name:'홍길동', age:55}, 20];
let onlyNum = arr4.filter( (item)=>{return typeof item === "number"} );

// 중괄호를 넣는다면 filter에서 조건식 전에 return을 적어주고
// 중괄호를 넣지않을거라면 return을 적지않고 조건식을 적어주면 된다.
```

<br>

**배열관련 함수 reduce** <br>
```
arr.reduce((sum,item)=> {},0) // sum은 누적시킬 때 사용할 변수, item은 배열 요소, 0은 sum의 초기값을 의미

let sumVal = sortedNum.reduce((sum,item)=>{return sum=sum+item),0);
```

<br>

**기본 배열을 내가 원하는 형태로 바꿀 때 map** <br>
```
let arr = [10,20,30,40];
let returnedArr = arr.map((item)=>{return item+'%'});
// 각 배열의 요소에 %를 추가한 새로운 배열을 만들어 낸다.

let orderList=[
            {oid:111, name:'홍길동',addr:'대구',tel: '010-111-2222', product:'모니터', 'pid':'111-222'},
            {oid:222, name:'남길동',addr:'울산',tel: '010-222-5555', product:'키보드', 'pid':'333-444'},
            {oid:333, name:'서길동',addr:'창원',tel: '010-333-3333', product:'SSD', 'pid':'555-666'},
            {oid:444, name:'동길동',addr:'김해',tel: '010-444-4444', product:'메인보드', 'pid':'777-442'},
        ]

let returnedMap = orderList.map((item)=>{
            return {oid:item.oid, tel:item.tel};
});
// oid와 tel만 존재하는 새로운 배열을 만들어 낸다.
```

<br>

**오픈 API를 통해 원하는 정보만 추출하기** <br>
```
const 한식 = 중구맛집_data.filter((item)=>{return item.FD_CS==='한식'});
// FD_CS(음식 카테고리)가 '한식'인 맛집만 추출

const 한식맛집 = 한식.map((item)=> {
            return {"BZ_NM": item.BZ_MN, "MNU:item.MNU};
});
// 한식인 식당의 식당명과 메뉴종류만 추출

MNU = MNU.split('<br />');
// Split을 이용한 배열처리. <br />을 기준으로 요소를 구분한다.
```
<br>

### ProtoType
Object객체 : 객체를 다루는 기본함수를 제공 <br>
Object.prototype  : 객체가 상속을 구현하는데 사용되는 메커니즘,Object객체 내에 구성 <br>
Object.prototype의 함수들
1. toString(): 객체를 문자열로 변환하여 반환한다.
2. hasOwnProperty(): 객체가 특정 속성을 직접 소유하고 있는지 여부를 확인한다.
3. isPrototypeOf(): 객체가 다른 객체의 프로토타입 체인에 존재하는지 여부를 확인한다.
4. valueOf(): 객체의 원시 값 표현을 반환한다.
5. toLocaleString(): 객체를 지역화된 문자열로 변환하여 반환한다.
6. propertyIsEnumerable(): 특정 속성이 열거 가능한 속성인지 여부를 확인한다.
7. constructor: 객체를 생성한 생성자 함수를 참조한다.

```
let obj = {name: '홍길동', age:55};
console.log(obj)
console.log(Object.keys(obj));
// 오브젝트가 가진 모든 key값을 배열로 가져온다
console.log(Object.values(obj));
// 오브젝트가 가진 모든 value값을 배열로 가져온다.
console.log(Object.entries(obj));
// [key, value]형태의 배열로 반환한다. [key배열,value배열]의 형태

let ob1 = {addr:'대구'}
let ob2 = {genter: 'M'}
console.log(Object.assign(obj,ob1,ob2));
// obj에 ob1 ob2속성을 복사할 수 있다.

Object.freeze(obj);
// 오브젝트를 더이상 수정할 수 없게끔 만든다.
Object.seal(obj);
// 새 속성 추가 불가
```

## JavaScript 연산자
### 산술 연산자
```
1. +
2. -
3. *
4. /
5. %
6. ++
7. --
```
<br>
```
++,--(증감연산자) : 변수안의 값을 1증가(++) or 1감소(--)에 사용되는 연산자 <br>
++a : a안의 값을 1증가한 뒤 다른 연산을 처리 <br>
a++ : 다른 연산처리 이후 a안의 값을 1증가 <br>
```
<br>

### 할당 연산자
```
1. =
2. += (더해서 할당)
3. -= (빼서 할당)
4. *= (곱해서 할당)
5. /= (나눠서 할당)
6. %= (나머지를 할당)
```
### 비교 연산자
```
1. ==
2. ===
3. !=
4. !===
5. >
6. <
7. >=
8. <=
   
console.log('123' == 123); // true
console.log('123' === 123); // false, value와 자료형을 함께 일치여부 확인
```
<br>

### 논리 연산자 & 비트 연산자
```
1. && (논리 AND) - 모든 조건식이 참이어야 참을 반환한다.
2. || (논리 OR) - 조건식 중 하나라도 참이면 참을 반환한다.
3. ! (논리 NOT)
4. & (비트 AND)
5. | (비트 OR)
6. ^ (비트 XOR)
7. ~ (비트 NOT)
8. << (왼쪽 시프트)
9. >> (오른쪽 시프트)
10. >>> (부호 없는 오른쪽 시프트)
```
<br>

### 삼항 조건 연산자
```
조건문 ? 참일 때 실행할 식 : 거짓일 때 실행할 식

let num=11;

(num>10) ? console.log(num,'은 10보다 큽니다.') : console.log(num,'은 10보다 작거나 같습니다.');
```
<br>

## JavaScript 흐름제어문
### if
```
if(조건문) {
            참일 때 실행문
} else if(조건문) {
            참일 때 실행문
} else {
            위의 조건이 모두 거짓일 때 실행문
}

if(window.innerWidth <= 400 ) {
            document.body.style.backgroundColor="green";
} else {
            document.body.style.backgroundColor="orange";
}
```
<br>

### for
```
// 기본 for
for(초기값;조건식;탈출연산식){}

document.write("<ul>");
for(i=1;i<=4;i++){
            document.write(`<li>${i}</li>`);
}
document.write("</ul>");

//----------------------------
// 개량 for
for( 인덱스 in 배열) {}

const data=중구맛집.data;
const one = data[0];
for(key in one) {
            console.log(key,one[key]);
}
```
<br>

## JavaScript 함수
**함수(function)** : 데이터를 받아 특정 처리를 하는 논리적 공간 <br>

1. 기본형태
   function 함수명(인자) {
            처리할 식
            return 반환할 값;
   }
   인자와 return값은 있어도, 없어도 된다.
   
3. 반환자료형의 Object처리
   여러개의 값을 반환해야한다면 Object를 만들어 하나만 반환한다.
   function f1(n1,n2,n3) {
            return {arg1:n1, arg2:n2, arg3:n3};
   }
   
5. 가변인자
   인자의 개수를 따로 지정하지 않는다.
   function f2(...args){
            console.log(args);
   }
   혹은 인자에 (n1,n2,...args)처럼 고정된 인자를 넣고 이후를 가변인자로 설정해도 된다.

<br>

**Hoisting** : 코드가 실행되기 전 변수선언/함수선언이 해당 스코프의 최상단으로 끌어 올려진 것 같은 현상 <br>
```
// 호이스팅 O
f1();
function f1() {
            console.log('f1함수 호출...');
}
f1();

// 함수가 전역처리 되어 첫번째 호출에도 함수가 실행되어진다.

// 호이스팅 X
// 익명함수의 경우 절차대로 진행되어야 한다.
f2(); // ERROR
const f2 = function() {
            console.log("f2함수 호출");
}
f2();
```
<br>
함수 표현식을 권장하는 이유 <br>
- 호이스팅 방식은 코드구조를 무너뜨린다. <br>
- 호이스팅 방식은 절차대로 처리되지 않아 혼란을 야기할 수 있다. <br>

<br>

**Closure 함수** <br>
내부함수가 외부함수의 변수를 사용할 수 있고, 외부함수는 내부함수가 실행되기전에 내부함수를 반환한다.
```
function outer(){
const func = ()=>{
            //상태값
            let num=0;

            //num의 값을 증가하는데 사용되는 함수
            const setNum = (n)=>{num+=n}

            //num의 값을 확인하는데 사용되는 함수
            const getNum = ()=>{
                console.log("getNum Call..")
                return num;
            }

            return { set: setNum, get: getNum};
        }
        const closure = func();
        console.log(closure.get());
```

<br>

**콜백함수(CallBack)** <br>
함수를 호출하는 시점이 바뀐 형태의 함수. <br>
기존방식: 사용자(개발자)가 함수를 직접 정의하고 정의된 함수를 호출(Call)하여 결과를 반환받는 방식. <br>
CallBack: 콜백함수의 인자로 로직이 담긴 함수(함수주소)를 전달하여 콜백함수로부터 처리된 결과를 반환받는 방식.

```
// 일반 함수
function func(n1,n2){
            console.log("func(n1,n2) Call!");
            return n1+n2;
}

// 콜백 함수
function callBackFunc(n1,n2,logic) {
            const v = logic(n1,n2);
            console.log(v);
}
callBackFunc(100,200,func);

// func의 함수 위치를 인자로 전달하고 콜백함수에서는 함수를 전달받고 내부적으로 실행한다.
// 즉, 함수를 인자로 받아 해당 함수를 이용하는 함수이다.

// 콜백 함수로 삽입정렬 만들기
function callBack3(array,func) {
            let tmp = 0;
            for(i=0; i<array.length-1;i++){
                        for(j=i+1;j<array.length;j++){
                                    if(func(array[j],array[i])<=0) {
                                                tmp=array[i];
                                                array[i] = array[j];
                                                array[j] = tmp;
                                    }
                        }
            }
}
arr2 = [10,2,4,5,1,3,5,7,6];
callBack3(arr2, (a,b)=>{return a-b});
```
<br>

## 이벤트 처리
### 기본노드검색
1. getElement
   - 단일 오브젝트를 반환한다. getElementById()
3. getElements
   - 배열 형태로 반환한다.
   - getElementsByClass()
   - getElementsByName()
   - getElementsByTag()
   - getElementsByTagNameNs()
3. querySelector()
   - 어떤 선택자든 들어올 수 있지만 단일 node만 선택한다. 선택자가 여러개의 node를 가리킬 경우 가장 첫번째 node를 선택한다.
5. querySelectorAll()
   - 어떤 선택자든 들어올 수 있고, 여러 node를 한번에 찾는다. nodelist형태로 가져오므로 배열 메서드를 사용할 수 있다.

<br>

**FORM 검색** <br>
```
// 모든 form찾기, 유사배열형태로 반환되고 (key, value)형태로 저장되어 있다.
const formEls = document.forms;

// 개별 form 접근
console.log(formEls[0]);
console.log(formEls[1]);
console.log(formEls[2]);

// name으로 개별 form에 접근
const formEl = document.frm2; // name="frm2"
formEl.userid.value='aaa';
formEl.action="abc.jsp"
formEl.submit();
// userid는 form안에 있는 input type의 name이고 action은 form을 전송할 곳을 지정한다.
```
<br>

**ClassList** <br>
해당 요소가 가지고 있는 모든 Class를 리스트화 해준다.<br>
add()와 remove()를 통해 class를 추가하고 삭제할 수 있다.
```
const btnEls = document.querySelectorAll('.btn');
btnEls.forEach((el,idx)=>{ // 탐색되는 요소요소마다 index를 부여하는데 그 index를 가져올 수 있다
   el.addEventListener('mouseover', ()=>{
            el.classList.add(`btn--st${idx}`);
   })
   el.addEventListener('mouseleave', ()=>{
            el.classList.remove(`btn--st${idx}`);
   })
})
```
<br>

### 이벤트처리
기본 형태 : .addEventListener('이벤트형태',(e)=>{이벤트})
<br>
1. 마우스
   - 'click' : 해당 element를 클릭했을 때
   - 'mouseover' : 마우스를 해당 element바깥에서 안으로 옮겼을 때
   - 'mouseleave' : 마우스를 해당 element안에서 바깥으로 옮겼을 때
   - 'dbclick' : 해당 element에서 더블 클릭했을 때
   - 'drop' : element를 드래그했다가 놓았을 때
   - clientX,clientY : 사용자 시점에서의 마우스의 X,Y좌표를 알 수 있는 속성
   - pageX, pageY : 페이지 시점에서의 마우스의 X,Y좌표를 알 수 있는 속성
3. 키보드
   - 'keyup': 키보드가 (내려간 상태에서) 올라올 때
   - 'keydown': 키보드가 내려갈 때
   - 'keypress': 키보드를 계속 누를 때
   - key : 해당 이벤트가 발생했을 때 눌러진 문자열을 나타낸다.
   - keyCode : 해당 이벤트가 발생했을 때 눌러진 문자열의 아스키코드를 나타낸다(keypress의 경우 아스키코드가 대소문자를 구분하지만
   - enter를 제외한 대부분의 escape문자를 인식하지 못한다.ex) alt,ctrl,tap,esc,backspace
6. 체크박스
   - 'change': 체크박스의 상태가 변화할 때
   - e.target.checked: 체크박스가 체크되어있으면 true를 체크되어있지않으면 false를 반환한다.
8. 스크롤
   - 'scroll': 스크롤 이벤트
   - window.scrollX : 문서의 수평 스크롤의 위치값을 반환한다. 뷰포트에서 가장 왼쪽의 가로축을 기준으로 한다.
   - window.scrollY : 문서의 수직 스크롤의 위치값을 반환한다. 뷰포트에서 가장 위쪽의 세로축을 기준으로 한다.
10. 사이즈조정
    - 'resize': 사이즈에 따른 이벤트
    - window.innerWidth : 브라우저 윈도우 두께를 제외한 실질적 가로너비
    - wondow.outerWidth : 브라우저 윈도우 두께를 포함한 전체 가로너비
12. 페이지로드
    - 'DOMContentLoaded': 사이즈 조정 이벤트는 사이즈가 변경되었을 때의 이벤트지 페이지가 로드되었을 당시의 사이즈에 이벤트가 적용되지 않는다.

<br>

### Node CRUD
1. 생성
   document.createElement('태그명') : 해당 태그명을 가진 요소를 생성한다. <br>
   '부모Node'.appendChild(대상) : 부모노드의 자식으로 대상을 추가한다. 이때 가장 아래에 추가된다. <br>
   '부모Node'.prepend(대상) :  부모노드의 자식으로 대상을 추가한다. 이때 가장 위에 추가된다. <br>
3. 삭제
   '부모Node'.removeChild(대상) : 부모노드의 자식들 중 대상을 제거한다. <br>
5. 수정
   input태그의 내용을 수정한다면 readOnly의 값을 true/false로 설정함에 따라 입력을 비활성/활성이 가능하다. <br>
   item.readOnly=true // 비활성화 <br>

## SYNC
**동기(Synchronous)** : 미리 약속된 규칙을 근거로 동작하는 방식, 절차대로 코드를 실행한다는 것. <br>
ex) 홈페이지 자체를 서버에서 받을 때 서버에 요청한 응답이 오기전까지는 아무것도 실행되지 않는 것.<br>
<br>
**비동기(Asynchronous)** : 약속된 규칙대로 동작하지 않고 특정한 방식으로 동작하는 방식, 절차대로 코드를 실행하지 않는다는 것. <br>
ex) 홈페이지 내에 부분적으로 요청을 보내고 응답을 받을 때 나머지 부분은 요청하던 말던 알아서 동작하는 것 <br>

1. **setTimeout** : 일정 시간 이후 특정작업을 수행한다. 변수로 저장하면 예약번호를 반환받을 수 있다.
   ```
   reservedId = setTimeout(() => {
      d1.innerHTML += "HELLOWORLD";
   }, 3000);
   ```
3. **clearTimeout** : setTimeout의 예약번호를 받아 해당 예약을 취소할 수 있다.
   ```
   clearTimeout(reservedId);
   ```
5. **setInterval** : 종료신호를 주기전까지 일정 주기로 코드를 계속 반복하여 실행한다. 변수로 저장하여 해당 작업의 index를 반환받는다.
   ```
   id=setInterval(()=>{
      box1.innerHTML+=`Batch start ${++count}`;
   },1000);
   ```
7. **clearInterval** : setInterval의 index를 받아 해당 작업을 취소할 수 있다.
   ```
   clearInterval(id);
   ```
9. **async/await**
    - async: 해당 함수가 비동기적인 처리를 하는 프로세스임을 암시
    - await: async블럭 내부에서 사용되며 다른 비동기 작업이 완료될때까지 대기하는 예약어
    - Promise: 비동기 요청 객체, 요청이 성공했을 때와 실패했을 때를 나누어 처리가 가능하다.
```
function sub_process_exe(val){
   return new Promise((resolve,reject)=>{
      setTimeout(()=>{
         resolve(val); // 비동기 요청이 성공했을 때 전달되는 값
      },3000);
   });
}

async function sub_process_func() {
await sub_process_exe(1)                                                                                                    
                .then((response)=>{
                    console.log('response',response);
                    sub1.innerHTML+=`${response}-Thread Run`
                })
                .catch(()=>{})

await sub_process_exe(2)
                .then((response)=>{
                    console.log('response',response);
                    sub2.innerHTML+=`${response}-Thread Run`

                })
                .catch(()=>{})
}
sub_process_func();
// 해당 함수를 실행시켜보면 동시에 동작하는 것이아니라 sub1,sub2가 순서대로 동작한다.
```
<br>
