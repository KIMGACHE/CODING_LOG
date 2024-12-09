# React
React는 Facebook에서 개발하고 유지관리하는 오픈 소스 자바스크립트 라이브러리로 사용자 UI를 구축하기 위해 사용된다. <br>

## React 특징 및 장점
1. 컴포넌트 기반 아키텍쳐
   - React는 UI를 독립적이고 재사용 가능한 컴포넌트로 분할할 수 있게 해준다. 각 컴포넌트는 자체적인 상태(state)와 속성(props)를 가지며, 이를통해 복잡한 UI를 관리하기 쉽게 만들어준다.
3. Virtual DOM
4. 단방향 데이터 흐름
   - React는 단방향 데이터 흐름을 사용하여 데이터가 부모 컴포넌트에서 자식 컴포넌트로 전달된다. 이 덕분에 데이터의 흐름을 추적하기 쉽게만들며, 애플리케이션의 상태 관리를 단순화한다.
6. JSX
   - JSX는 JavaScript XML의 약자로, 자바스크립트 코드 안에서 HTML과 유사한 구문을 사용할 수 있도록 해준다. 코드의 가독성을 높여주고 React 컴포넌트를 작성하는 데 유용하다.
8. React Hooks(중요)
9. 서버사이드 렌더링

## 시작?
1. React App 생성
```
폴더를 하나 생성하여 해당 폴더의 cmd창을 열어 커맨드 입력
npx create-react-app '프로젝트명'
------------------------------------------------------------------------------
import logo from './logo.svg';
import './App.css';

function App() {
  let title = "제목부분 입니다";
  const st = {color:"orange"}

  return (
    <>
      <div className="top-header">
        <h1 style={{color:"gray",backgroundColor:"black"}}>{title}</h1>
        Hello, World.
      </div>
      <div className="nav" style={st}>
        World, Hello.
      </div>
    </>
  );
}

export default App;

```
**반드시 return아래에는 태그가 존재해야하고 단 하나의 (상위)태그만이 존재해야한다.** <br>
**html과 다르게 class가 아니라 className을 사용한다.** <br>
**return이전 부분에 변수를 선언할 수 있고 이 변수를 사용할 때에는 {}안에 변수명을 넣어준다.** <br>
**style의 경우 json type으로 내용을 받아오기 때문에 {}내부에 다시 json형식인 {}를 써서 style을 지정한다.**


## JSX
### basic
```
const basic = ()=>{


    return (
        <>
            <h1>Basic Component</h1>
        </>
    );
}

export default basic;

--> basic.js파일을 위와 같이 생성한 뒤 App.js에서 불러올 수 있다
import basic from './JSX/basic';

      <div>
        <basic />
      </div>
```

```
const basic1 = ()=>{


    return (
        <>
            <h1>Basic1 Component</h1>
        </>
    );
}

const basic2 = ()=>{


    return (
        <>
            <h1>Basic2 Component</h1>
        </>
    );
}

const basic3 = ()=>{


    return (
        <>
            <h1>Basic3 Component</h1>
        </>
    );
}

export default {basic1,basic2};

--> 이렇게 default가 여러개의 함수로 이루어진 경우
--> App.js에서 .basic1 , .basic2로 접근 가능하다.

import basic from './JSX/basic';

      <div>
        <basic.basic1 />
      </div>
```

return할 문장이 하나인 경우
```
const basic3 = ()=>{

    return <h1>Basic3 Component</h1>
}
--> return의 ()를 생략할 수 있다.

const basic3 = <h1>Basic3 Component</h1>
--> 화살표 함수도 생략가능하다.
```

export default가 아니라 export로 가져오는 함수의 경우
```
import {basic3} from './JSX/basic';
--> ./JSX/basic에서 export하는 함수들 중에서 특정 함수만을 가져올 때 {}를 사용한다. 이때, {}안에는 함수명이 들어가야한다.
```

외부의 값을 받아오는 props
```
const Tmp = (props) => {
   if(props)
      return <h1>Hello ? {props.title}</h1>
   else
      return <h1>Hello</h1>
    );
}

export const basic4 = <Tmp title="basic4_Test" />
export const basic5 = <Tmp />
--> component의 이름은 대문자로 시작해야 한다.
```

```
const Tmp2 = (props) => {
    return(
        <>
            <ul>
                {props.data.map((el)=>{
                    console.log(el);
                    return (
                        <li>{el}</li>
                    );
                })}
            </ul>
            <ul>
                {props.data.map((el)=><li>{el}</li>)}
            </ul>
        </>
    );
}
--> return 내부에서 한번 더 return 할 수 있음
```

### Event
**클릭 이벤트**
```
const EventComponent1 = () => {
    return (
        <button onClick={(e)=>{console.log("EventComponent1",e)}}>버튼1</button>
    );
}
export default {
    EventComponent1,
}

import EC from './JSX/Event';

<EC.EventComponent />
```

함수 내부에 이벤트를 정의
```
const EventComponent2 = () => {
    const handleClick2 = (e)=>{console.log("EventComponent2",e)}
    return (
        <button onClick={handleClick2}>버튼2</button>
    );
}
```

**키보드이벤트**
```
const EventComponent3 = () => {

    const handleKeyDown = (e) => {
        console.log("KeyDownEvent",e.keyCode)
    }

    return (
        <input onKeyDown={handleKeyDown}/>
    );
}
```






















