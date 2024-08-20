## HTML

**HTML이란?** Hyper Text Markup Language의 약어<br>
**HyperText** : 웹페이지에서 다른 페이지로 이동할 수 있도록 하는 것<br>
<br>
**Element** : 요소, 여는 태그(Tag) + 내용(Contents) + 닫는 태그(없는 경우도 있음)<br>
**DTD(DOCTYPE or Document Type Definition)** : HTML 문서의 최상위에 위치하는 것으로 해당 문서의 문서타입을 알려주는 역할을 한다.

**유용한 단축키**
1. 주석처리 : ctrl + /
2. 라인복사 : shift + alt + 방향키 아래
3. 기본구조 : !를 입력하고 tap 혹은 enter키 (vs code기준)
4. 자동정렬 : alt + shift + f

<br>

**태그는 line형태와 block형태로 나뉘어진다.** <br>
block형태의 경우 하나의 행을 차지한다.
line형태의 경우에는 행의 구조를 바꾸지 않으며 특별한 스타일을 부여하고 싶을 때 사용한다. <br>
```
<span style=”color:red;background-color:black”>
```

<br>

### 단락 태그
<p></p> : 위,아래 여백을 주는 단락을 만들어 주는 태그 <br>
<div></div> : 한 라인을 통째로 사용하는 단락을 만드는 태그 (block) <br>
<span></span> : line형태의 단락을 만드는 태그 <br>

### 엔티티(Entity)
HTML에는 미리 예약된 몇몇 문자가 있으며 HTML예약어라고 부른다. <br>
엔티티의 형태는 다음과 같다. <br>
```
&엔티티이름;
또는
&엔티티숫자;

ex) &nbsp; 는 공백을 의미한다.
```

### 리스트형 구조생성 태그
순서가 없는 리스트 : unordered list, <ul></ul>
순서가 있는 리스트 : ordered lsit, <ol></ol>
```
    <ul>
      <li>List1</li>
      <li>List2</li>
      <li>List3</li>
      <li>List4</li>
    </ul>

    <ol type="i">
      <li>List1</li>
      <li>List2</li>
      <li>List3</li>
      <li>List4</li>
    </ol>
```

### EMMET
반복적인 구조나 코드를 쉽게 입력하는 것을 도와준다. <br>

1. 자식요소를 만들 때 '>'를 사용한다.
   ```
   div>ul>li
   ```
3. 형제요소(같은 레벨)를 만들 때 '+'를 사용한다.
   ```
   div>ul+ol
   div>p+div>span
   ```
5. 부모태그(상위태그)로 이동할 때 '^'를 사용한다.
   ```
   div>ul>li^p
   ```
7. 반복처리를 할 때에는 '*'를 사용한다.
   ```
   div>ul>li*4
   ```
9. 문자열을 넣고싶을 때에는 '{문자열}'을 사용한다.
   ```
   div>ul>li*4>a{기본메뉴$}
   div>ul>li*4>a{기본메뉴$@5} - 시작 번호를 5부터 하겠다는 의미
   ```

### 요소 선택자
class : 그룹으로 묶어서 처리할 때 사용 <br>
id : 낱개로 하나하나 처리할 때 사용 (문서 내에서 유일한 값을 가져야 한다.) <br>
<br>
여는 태그에 class="class명"을 통해 지정할 수 있다.
여는 태그에 id="id명"을 통해 지정할 수 있다.
<br>
class를 사용할 때에는 **.class명** 으로 지정하여 사용한다.
id를 사용할 대에는 **#id명** 으로 지정하여 사용한다.

### 테이블
```
    <table>
        <caption>제목</caption> -> 테이블의 이름을 지정할 수 있다.
        <tr> -> 테이블의 행을 구성하는 태그
            <th>1</th> -> 테이블의 열을 구성하는 태그이면서 가장 위에 있는 행에 위치한 열을 구성하는 태그
            <th>2</th>
            <th>3</th>
            <th>4</th>
        </tr>
        <tr>
            <td>5</td> -> 테이블의 열을 구성하는 태그
            <td>6</td>
            <td>7</td>
            <td>8</td>
        </tr>
        <tr>
            <td>9</td>
            <td>10</td>
            <td>11</td>
            <td>12</td>
        </tr>
    </table>
```
열 병합과 행 병합
1. 열 병합 (colspan)
```
    <table>
        <tr>
            <td colspan="2">1</td> -> 2개의 열을 병합하겠다는 의미로 주석처리된 2번의 위치까지 1번 열이 병합한다.
            <!-- <td>2</td> -->
            <td>3</td>
            <td>4</td>
        </tr>
        <tr>
            <td>5</td>
            <td>6</td>
            <td>7</td>
            <td>8</td>
        </tr>
        <tr>
            <td>9</td>
            <td colspan="3">10</td> -> 3개의 열을 병합하겠다는 의미로 주석처리된 11,12번 위치까지 10번 열이 병합한다.
            <!-- <td>11</td>
            <td>12</td> -->
        </tr>
        <tr>
            <td>13</td>
            <td>14</td>
            <td colspan="2">15</td> -> 2개의 열을 병합하겠다는 의미로 주석처리된 16번의 위치까지 15번 열이 병합한다.
            <!-- <td>16</td> -->
        </tr>
    </table>
```
3. 행 병합 (rowspan)
```
<table>
        <tr>
            <td rowspan="2">1</td> -> 2개의 행을 병합하겠다는 의미로 주석처리된 5번의 위치까지 1번 행이 병합한다.
            <td>2</td>
            <td>3</td>
            <td rowspan="3">4</td> -> 3개의 행을 병합하겠다는 의미로 주석처리된 8, 12번의 위치까지 4번 열이 병합한다.
        </tr>
        <tr>
            <!-- <td>5</td> -->
            <td rowspan="2">6</td>
            <td>7</td>
            <!-- <td>8</td> -->
        </tr>
        <tr>
            <td>9</td>
            <!-- <td>10</td> -->
            <td>11</td>
            <!-- <td>12</td> -->
        </tr>
        <tr>
            <td>13</td>
            <td>14</td>
            <td>15</td>
            <td>16</td>
        </tr>
    </table>
```

### 앵커 태그
<a href=""></a>의 구조로 앵커 태그의 내용을 클릭했을 때 해당 링크로 이동된다.
```
<a href="https://www.naver.com">NAVER 이동</a>
<a href="https://www.naver.com" target="_blank">NAVER 이동(새로운 탭)</a>
<a href="./02Basic.html">02Basic.html이동</a>
```
target 속성의 '_blank'를 이용하면 새로운 웹페이지를 열어 해당 링크로 이동할 수 있다. <br>
링크에 문서의 위치를 입력하면 해당 문서를 열어볼 수 있다. <br>
html문서에 요소 선택자를 이용하여 원하는 요소를 선택하고 앵커태그의 링크에 해당 요소로 이동할 수도 있다. <br>
id="HTML" -> <a href="#HTML">HTML</a> <br>

### 이미지 태그
구조 : <img src="" alt=""></img> <br>
src : 이미지파일의 경로
alt : 이미지에 문제가 생겼을 때 표시할 텍스트
```
<img src="./images/다람쥐.jpg" alt=”다람쥐">
<img src="https://cdn.imweb.me/upload/S201910012ff964777e0e3/62f9a36ea3cea.jpg" alt="강아지">
```
외부에서 이미지를 가져올 수도 있고 local에서 이미지를 가져올 수도 있다.

### 비디오 태그
```
<video src="./videos/video1.mp4" type="video/mp4">
    
</video>

<video>
    <source src="./videos/video1.mp4" type="video/mp4">
</video>
```
위의 방법은 하나의 비디오를 삽입할 때 사용하는 방식이고, 아래 방법은 여러개의 source를 삽입할 때 사용하는 방식으로 source태그를 여러개 열어 여러 개의 source를 삽입할 수 있다. <br>
비디오 태그의 속성에는 **controls**(재생버튼), **autoplay**(자동재생), **muted**(음소거,정책상 자동재생 속성을 사용하려면 음소거가 필요한 경우가 있다), **loop**(재생이 끝나도 반복적으로 재생한다) <br>

유튜브 영상을 가져오고 싶다면 해당 영상-공유-퍼가기에 있는 코드를 복사하여 src에 복사한다.<br>
영상 링크에 &autoplay=1&mute=1을 붙임으로써 자동재생 시킬 수 있다. <br>

### Form 태그
사용자로부터 특정 정보를 받아 서버로 전달하는데 사용되는 태그
<form action="" method=""></form> <br>
action : 전달받는 서버 API() or EndPoint <br>
method : 서버로 요청하는 방식 <br>

**GET** : 사용자 요청 정보를 Query String으로 전달 (default) <br>
**POST** : 사용자 요청 정보를 Request Body에 담아 전달 (optional) <br>
- PUT : <br>
- PATCH : <br>
- DELETE : <br>

<br>

Form에 정보를 입력하는 Input 태그의 종류
```
<input type="text"/>        -> 텍스트 입력
<input type="password"/>    -> 비밀번호 입력, 입력한 값이 보이지 않는다.
<input type="email"/>       -> 이메일 형식의 입력값이 아니면 입력을 허용하지 않는다.
<input type="number"/>      -> 숫자 입력, 카운트의 최소값(min), 최대값(max), 카운트당 몇이 오를것인가(step) 등을 설정가능
<input type="tel"/>         -> 전화번호 입력, 원하는 형식을 지정할 수 있다. ex) pattern="[0-9]{3}-[0-9]{4}-[0-9]{4}"

<input type="radio" name="gender" value="M"/>남자    -> 여러개 중 하나만을 선택해야 할 때
<input type="radio" name="gender" value="F"/>여자    -> name이 같아야하고 실제 전달되는 값인 value를 다르게 설정한다.

<input type="checkbox" name="hobby" value="game"/>게임    -> 여러개 중 중복하여 선택할 수 있다.
<input type="checkbox" name="hobby" value="game"/>게임    -> 마찬가지로 name이 같고, value를 다르게 설정한다.

<input type="file"/>        -> 파일 입력, multiple옵션을 통해 여러개의 파일을 입력받을 수 있다.
<input type="date">         -> 날짜 입력, 연월일을 지정할 수 있으면 yyyy-mm-dd형식으로 전달된다.
<input type="datetime-local">    -> 연월일과 시분가지 입력할 수 있다. ex) date=2024-08-20T12%3A50
<input type="color">        -> 색상 입력, HTML Color Code형식으로 값이 전달된다.
<input type="url">          -> url 입력, url형식이 맞는지 아닌지 검사한다.
<input type="range">        -> 범위 입력, 최소값(min), 최대값(max), 시작값(value)를 지정할 수 있다.

<select name="location">                -> 여러값 중 하나만을 선택 할 수 있다.
    <option value="대구">대구</option>   -> selected 옵션을 통해 기본값을 설정할 수 있다.
    <option value="부산" selected>부산</option>
</select>

<textarea rows="10" cols="50"></textarea> -> 텍스트 입력을 받는 공간을 설정한다.
```

### 정규표현식
문자열을 처리하는 방법 중의 하나로 특정한 조건의 문자를 검색하거나 치환하는 과정을 매우 간편하게 처리 할 수 있도록 하는 수단이다. <br>
```
^(?=.*[A-Za-z])(?=.*\d)[A-Za-z\d]{8,}$

^ : 문자열의 시작을 의미 <br>
$ : 문자열의 끝을 의미 <br>
(pattern) : 패턴을 구분하는 부분식
(?=pattern) : 앞에서부터 끝까지 패턴을 탐색하겠다는 의미
. : 모든 문자 일치
* : 앞의 문자나 부분식이 0개 이상 그리드 탐색
[A-Za-z] : 영어 알파벳(대/소문자)이 하나 이상 포함되어야 한다
(?=.*\d) : 어떤 위치에서든지 이후에 숫자가 하나 이상 포함되었는지 확인한다.
\d : 0~9까지의 숫자, [0~9]와 같다
[A-Za-z\d] : 대/소문자, 숫자중에 하나 이상 포함되어야 한다는 의미
{8,} : 8글자 이상이어야 하고 최대글자의 제한은 없다는 의미
```
