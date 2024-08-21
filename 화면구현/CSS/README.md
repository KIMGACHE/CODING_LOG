## CSS

**CSS를 적용시키는 방법**
1. Style 태그를 이용하는 방법
2. 외부 css파일 제작 후 link하는 방법
3. inline style을 적용하는 방식

<br>

**태그의 종류**
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

**Style 속성**
width : 너비 <br>
height : 높이 <br>
margin : 요소와 요소와의 간격, 예를 들어 20px로 설정했다면 상하좌우 20px로 설정된다. <br>
padding : border(테두리)와 contents(내용)사이의 간격, 예를 들어 20px로 설정했다면 상하좌우 20px로 설정된다. <br>
border : 테두리 <br>




