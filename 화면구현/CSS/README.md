## CSS

### CSS를 적용시키는 방법
1. Style 태그를 이용하는 방법
2. 외부 css파일 제작 후 link하는 방법
3. inline style을 적용하는 방식

<br>

### 태그의 종류
1. **Block Tag** = 한 행 전체를 차지하는 태그
   - width, height, margin, padding 설정이 가능하다.
3. **Line Tag** = 한 행안에 포함되어지는 태그
   - width, height 설정이 불가하고 margin의 경우 left,right만 설정가능하고 padding은 설정 가능하다.
5. **Inline-Block Tag** = 한 행안에 포함되어지는 태그
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
**width** : 너비, default값은 auto로 브라우저의 너비만큼 넓어진다. <br>
**height** : 높이, defualt값은 auto로 최소한의 높이를 사용한다. 즉 auto고 내용이 없다면 높이가 0이 된다. <br>
**margin** : 요소와 요소와의 간격, 예를 들어 20px로 설정했다면 상하좌우 20px로 설정된다. <br>
**padding** : border(테두리)와 contents(내용)사이의 간격, 예를 들어 20px로 설정했다면 상하좌우 20px로 설정된다. <br>
**border** : 테두리 <br>

**min-width** : 최소 너비 <br>
**max-width** : 최대 너비 <br>
**min-height** : 최소 높이 <br>
**max-height** : 최대 높이 (height가 auto인 경우에는 작아지려는 성질때문에 max-height가 의미가 없다.) <br>

* 자식이 부모보다 z-index값이 높다. <br>

<br>

### Color
**색상을 표현하는 방식** <br>
1. **자체 예약어**를 사용하는 방식
2. **rgb(r,g,b,)** 함수를 사용하는 방식, 각 값은 0~255값으로 이루어진다.
3. **rgba(r,g,b,a)** 함수를 사용하는 방식, 각 rgb값은 0~255값으로 a값은 0~1로 이루어지며 0에 가까울 수록 투명하고 1에 가까울 수록 불투명하다.
4. **HTML 컬러코드**를 사용하는 방식, ex) #FF0000, 2자리씩 16진수로 r,g,b를 표현하는 것이다.

<br>

### Unit
**px** : 고정크기 <br>
**%** : 부모를 기준으로 백분율만큼 크기를 지정한다. <br>
**vw,vh** : viewport를 기준으로 백분율만큼 크기를 기정한다. (viewport: 웹페이지가 이용자에게 보여지는 화면) <br>
**em** : 부모의 글자크기를 단위로 크기를 지정한다. <br>
**rem** : root(기본글자크기)를 단위로 크기를 지정한다. (default값은 16px이다.) <br>

font-size: clamp(최소값, 기준값, 최대값); <br>
글자 크기를 기준값으로 설정하나, 만약 기준값이 가변 크기라면 그 크기를 최소/최대값으로 제한한다는 의미. <br>
<br>
### Background
**background-image**: url('이미지링크'); <br>
**background-size**: auto, cover, contain; <br>
- cover의 경우 이미지의 배율을 무시하고 화면을 채우게 된다. <br>
- contain의 경우 이미지의 배율을 지켜 이미지를 보여준다. <br>
**background-repeat**: no-repeat; <br>
- background의 size가 contain이면 배경이 반복되는 것이 default값이고, 이를 방지하기 위한 설정값. <br>
b**ackground-attachment**: <br>
- background의 배치를 설정한다. <br>

<br>

### TEXT
1. **글자 간격** <br>
   letter-spacing: 자간 <br>
   word-spacing: 단어와 단어 사이의 간격 <br>
3. **글자 위치** <br>
   text-align: left, center, right; 수평 정렬방식<br>
   line-height: line-box의 높이를 설정하는 속성으로 일반적으로 텍스트 줄 사이의 거리를 설정하는데 사용된다.<br>
5. **글자 Decoration** <br>
   overline : text 위에 줄 긋기 <br>
   underline : text 아래에 줄 긋기 <br>
   line-through : text 중앙에 줄 긋기 <br>
   none : 아무 설정도 없다.(default) <br>
7. **폰트 굵기** <br>
   font-weight: 100 ~ 900; <br>
   100 ~ 900사이의 값으로 굵기를 지정할 수 있다. (400이 default값)<br>

### Font-Family
1. 자체 폰트 사용
   font-family: 상태에서 crtl + space를 누르면 목록이 나온다.
3. 외부 링크 참조
5. 폰트 다운로드 후 적용
   폰트 다운로드 후 style태그 내에
   ```
   @font-face {
      font-family: "dongle"; -> 폰트 이름지정
      src: url("./fonts/Dongle-Regular.ttf"); -> 다운받은 폰트 경로
      font-weight: 400; -> 폰트 굵기 설정
      font-style: normal; -> 폰트 스타일 설정
   }
   이후 font-family: 'dongle'; 로 사용
   ```
<hr>

### BOX
#### Box의 Margin
1. **margin: 10px;** <br>
   - top, right, bottom, left 모두 10px로 margin을 설정한다. <br>
3. **margin: 10px 20px;** <br>
   - (top, bottom)은 10px, (right, left)는 20px로 margin을 설정한다. <br>
5. **margin: 10px 20px 30px;** <br>
   - top은 10px, (right,left)는 20px, bottom은 30px로 margin을 설정한다. <br>
7. **margin: 10px 20px 30px 40px;** <br>
   - top:10px, right:20px, bottom:30px, left:40px로 margin을 설정한다. <br>

**※ margin-(방향)을 통해 원하는 방향에만 margin을 적용할 수도 있다.** <br>
ex) margin-top: 100px; <br>
<br>
기본적으로 margin은 시계방향으로 설정할 수 있다. <br>

#### Box의 Padding
1. **padding: 10px;** <br>
   - top, right, bottom, left 모두 10px로 padding을 설정한다. <br>
3. **padding: 10px 20px;** <br>
   - (top, bottom)은 10px, (right, left)는 20px로 padding을 설정한다. <br>
5. **padding: 10px 20px 30px;** <br>
   - top은 10px, (right,left)는 20px, bottom은 30px로 padding을 설정한다. <br>
7. **padding: 10px 20px 30px 40px;** <br>
   - top:10px, right:20px, bottom:30px, left:40px로 padding을 설정한다. <br>

**※ padding-(방향)을 통해 원하는 방향에만 padding을 적용할 수도 있다.** <br>
ex) padding-top: 100px; <br>
<br>
기본적으로 padding은 시계방향으로 설정할 수 있다. <br>

#### Box Sizing 
**box-sizing: border-box;** <br>
contents box + border + padding의 길이를 모두 합쳐서 너비나 높이를 설정한다.<br>
<br>
**box-sizing: content-box;(default)** <br>
너비나 높이가 contents box의 크기로만 설정된다. border나 padding의 경우 너비와 높이에 더해진다.<br>

<hr>

### Border
**border:(굵기) (스타일) (색상);** 과 같이 테두리를 설정할 수 있다.
```
ex) border: 1px solid red;
```
<br>

**※ margin과 padding처럼 특정 방향에만 border를 적용시킬 수 있다.**
```
ex) border-right: 3px dashed green;
```
<br>
스타일에는 solid(실선), dashed, dotted(점선), double(두줄) 등등이 있다.<br>
<br>

<hr>

**테두리의 꼭짓점** <br>
border-radius: 15px; <br>
반지름이 15px인 원으로 꼭짓점을 잘라냈다. <br>
border-radius: 15px 35px; <br>
(좌측상단, 우측하단)을 15px, (우측상단, 좌측하단)을 35px씩 꼭짓점을 잘라냈다. <br>
border-radius: 10px 50px 100px; <br>
좌측상단을 10px, (우측상단, 좌측하단)을 50px, 우측하단을 100px씩 꼭짓점을 잘라냈다. <br>
border-radius: 10px 30px 50px 100px; <br>
좌측상단을 기준으로 시계방향으로 적용한다. <br>

<hr>

#### OverFlow
자식태그가 부모태그보다 더 커지는 경우에 overflow속성을 통해 수정할 수 있다.<br>
overflow: auto; -> 스크롤을 만들어준다.<br>
overflow: hidden; -> 넘친부분을 가려준다.<br>

<hr>

### 선택자
**전체 선택자(*)** : 모든 요소에 공통적으로 적용된다. <br>
**요소 선택자(요소명)** : 해당 문서내에 해당 이름의 모든 요소에 대해 적용된다. <br>
**id 선택자(#)** : 유일한 요소에 대해 적용된다. <br>
**class 선택자(.)** : 같은 class로 묶인 요소들에 대해 적용된다. <br>
**group 선택자(,)** : 여러개의 선택자에 동시에 적용된다. <br>
<br>
**자식 선택자(>)** : 자신의 자식요소에만 적용된다. <br>
**자손 선택자(' ')** : 자신의 자식과 자식의 자식들 모두에게 적용된다. <br>
<br>
**동위 선택자(~)** : 같은 Depth의 하위(깊이의 개념에서의 하위가 아니라 절차상에서의 아래) 모든 선택자에 적용된다. <br>
**동위 선택자(+)** : 같은 Depth의 하위(깊이의 개념에서의 하위가 아니라 절차상에서의 아래) 1개의 선택자에 적용된다. <br>


