## CSS

### CSS를 적용시키는 방법
1. Style 태그를 이용하는 방법
2. 외부 css파일 제작 후 link하는 방법
3. inline style을 적용하는 방식

<br>

### 태그의 종류
1. Block Tag = 한 행 전체를 차지하는 태그
   - width, height, margin, padding 설정이 가능하다.
3. Line Tag = 한 행안에 포함되어지는 태그
   - width, height 설정이 불가하고 margin의 경우 left,right만 설정가능하고 padding은 설정 가능하다.
5. Inline-Block Tag = 한 행안에 포함되어지는 태그
   - width, height, margin, padding 설정이 가능하다.

<br>

기본적으로는 태그의 종류가 각 태그마다 적용되어 있지만, <br>
```
display: block;
display: inline;
display: inline-block;
```
위의 코드로 임의 적용가능하다.

<br>

### Style 속성
width : 너비, default값은 auto로 브라우저의 너비만큼 넓어진다. <br>
height : 높이, defualt값은 auto로 최소한의 높이를 사용한다. 즉 auto고 내용이 없다면 높이가 0이 된다. <br>
margin : 요소와 요소와의 간격, 예를 들어 20px로 설정했다면 상하좌우 20px로 설정된다. <br>
padding : border(테두리)와 contents(내용)사이의 간격, 예를 들어 20px로 설정했다면 상하좌우 20px로 설정된다. <br>
border : 테두리 <br>

min-width : 최소 너비 <br>
max-width : 최대 너비 <br>
min-height : 최소 높이 <br>
max-height : 최대 높이 (height가 auto인 경우에는 작아지려는 성질때문에 max-height가 의미가 없다.) <br>

* 자식이 부모보다 z-index값이 높다. <br>

<br>

### Color
색상을 표현하는 방식
1. 자체 예약어를 사용하는 방식
2. rgb(r,g,b,)함수를 사용하는 방식, 각 값은 0~255값으로 이루어진다.
3. rgba(r,g,b,a)함수를 사용하는 방식, 각 rgb값은 0~255값으로 a값은 0~1로 이루어지며 0에 가까울 수록 투명하고 1에 가까울 수록 불투명하다.
4. HTML 컬러코드를 사용하는 방식, ex) #FF0000, 2자리씩 16진수로 r,g,b를 표현하는 것이다.



























