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
<a href="https://www.naver.com">NAVER 이동</a> -> NAVER 이동이라는 텍스트를 클릭하는 경우 해당 주소로 이동한다.
```


