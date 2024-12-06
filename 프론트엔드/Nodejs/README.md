# Spring
Chrome V8 JavaScript 엔진으로 빌드된 JavaScript 런타임 <br>
Javascript 를 실행 시킬 수 있도록 하는 오픈소스 서버 환경 <br>
Java를 개발하기 위해 JRE(JVM) 를 설치하는 것과 같은 원리 <br>

cf)
Chrome V8 JavaScript 엔진
 - 구글에서 제작한 자바스크립트 엔진
 - 여기서 자바스크립트 엔진이란 자바스크립트 코드를 실행하는 프로그램 또는 인터프리터를 뜻한다.

JavaScript 런타임
 - 런타임은 프로그래밍 언어가 구동되는 환경을 말한다.
 - 즉, JavaScript 언어가 구동되는 환경.

## Node.js특징
1. 무료
2. OS에 종속적이지 않음
3. 비동기 프로그래밍을 사용한다.
4. 단일 스레드이다.

## Node.js설치
1. nodejs검색 후 최신버전 다운로드
2. NPM 설치
3. npm init -y
4. npm install parcel-bundler -D

(NPM : Node Package Manager,Node.js 환경에서 사용 가능한 패키지를 다운 받을 수 있게 하는 도구) <br>
(npm install parcel-bundler -D 명령어는 현재 프로젝트에 parcel-bundler를 개발 시에 사용할 패키지로 설치.) <br>

## .ignore
gitignore.io 페이지로 가서 node라고 검색하면 나오는 내용을 복사하여 .gitignore파일을 만들어 붙여넣으면 끝


## SCSS
SASS란 대표적인 CSS 전처리기 중 하나이다.
CSS가 동작하기 전에 사용하는 기능으로 CSS와 문법은 유사하지만 선택자의 중첩이나 조건문, 반복문 등을 사용하여 더 편리하게 작성할 수 있다.

SCSS란 Sass의 3버전에서 등장한 것으로 css와 거의 같은 문법으로 Sass기능을 지원한다.
**프로젝트 생성**
```
- Step 1
    - npm init -y 
- Step 2
    - npm i -D parcel-bundler
- Step 3
    - package.json->
    - "scripts": {
         "dev" : "parcel 01.html",
      "build" : "parcel build 01.html" 
    - },
- Step 4
    - npm run dev 
```

### 중첩
```
.container {
  border: 1px solid;
  width: 500px;

  ul {
    border: 1px solid white;
    width: 300px;
  }
}
```
위의 코드의 경우 class가 container인 div의 스타일과 container의 자식 ul의 스타일을 적은것 <br>
기존의 css와 달리 중첩하는 방식으로 코드를 쓴다.

### 변수
```
$globalSize : 250px;    // 변수 선언

.container {
    border: 1px solid;
    width: $globalSize;
    margin: 50px;

    $c1Height : 100px;   // 동일한 계층과 하위 계층에서만 사용가능한 변수
    .item {
        width: $globalSize;
        height: $c1Height;
        background-color: royalblue;
    }
}
```
$를 사용해
