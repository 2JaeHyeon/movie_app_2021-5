# 이재현 201840223
<hr>
※ 첫 글자 사용시 대문자 사용<br>
function으로 정의 내린 것을 (컴포넌트)라고 칭한다<br>
컴포넌트는 자바스크립트와 HTML을 조합한 JSX라는 문법을 이용<br>
JSX의 문법은 JS와 HTML문법의 조합한 것<br>
npm install axios 설치 <br>
npm install <br>

## https://ko.reactjs.org/

npx create-react-markdown-deitor<br>
설치 npm install remarkable<br>
npm start<br>
시간 나오는 : Date().toLocaleTimeString() <br>
<hr>
react에는 함수 컴포넌트와 클래스 컴포넌트가 있다 <br> 
★ 컴포넌트의 이름은 항상 <b>대문자</b>로 ★ <br>
컴포넌트 합성 : 컴포넌트는 출력에 다른 컴포넌트를 참조할 수 있다.<br>
<hr>

# 12월 01일
** 함수형 / 클래스형 2개가 있다.**  

다섯 단계로 Clock과 같은 함수 컴포넌트를 클래스로 변환할 수 있습니다.  

React.Component를 확장하는 동일한 이름의 ES6 class를 생성합니다.  
render()라고 불리는 빈 메서드를 추가합니다.  
함수의 내용을 render() 메서드 안으로 옮깁니다.    
render() 내용 안에 있는 props를 this.props로 변경합니다.  
남아있는 빈 함수 선언을 삭제합니다.  
```
class Clock extends React.Component {
  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.props.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}
```
### 클래스에 로컬 State 추가하기
render() 메서드 안에 있는 this.props.date를 this.state.date로 변경합니다.  
```
class Clock extends React.Component {
  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        ■<h2>It is {this.state.date.toLocaleTimeString()}.</h2>■
      </div>
    );
  }
}
```
초기 this.state를 지정하는 class constructor를 추가
초기화 시켜준다.    
```
class Clock extends React.Component {
  constructor(props) {
    super(props);
   ■ this.state = {date: new Date()}; ■
  }

  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}
```
여기서 어떻게 props를 기본 constructor에 전달하는지 유의  
```
  constructor(props) {
   ■ super(props); ■
    this.state = {date: new Date()};
  }
```
클래스 컴포넌트는 항상 props로 기본 constructor를 호출 

<.Clock /> 요소에서 date prop을 삭제  
```
ReactDOM.render(
 ■ <Clock />, ■
  document.getElementById('root')
);

```
## 결과 
```
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }

  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}

ReactDOM.render(
  <Clock />,
  document.getElementById('root')
);
```
## 생명주기 메서드를 클래스에 추가

많은 컴포넌트가 있는 애플리케이션에서   컴포넌트가 삭제될 때  해당 컴포넌트가 사용 중이던 리소스를 확보하는 것이 중요  

Clock이 처음 DOM에 렌더링 될 때마다 타이머를 설정  이것은 React에서 **“마운팅”**  

Clock에 의해 생성된 DOM이 삭제될 때마다 타이머를 해제  이것은 React에서 **“언마운팅”**  

컴포넌트 클래스에서 특별한 메서드를 선언하여 컴포넌트가 마운트되거나 언마운트 될 때 일부 코드를 작동
```
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }
■
■  componentDidMount() {
    갱신해주는 역할  
■  }
■
■  componentWillUnmount() {
■  } 

  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}
```
이러한 메서드들은 **생명주기 메서드**라고 한다.  

## setState()에 대해서 알아야 할 세 가지
> 직접 State를 수정 X  
this.state를 지정할 수 있는 유일한 공간은 바로 constructor
>

```
this.state.comment = 'Hello';  X
this. ■set■ State({comment: 'Hello'}); O
```
>State 업데이트는 비동기적일수 있다.  
this.props와 this.state가 비동기적으로 업데이트될 수 있기 때문  
>
```
this.setState({
  counter: this.state.counter + this.props.increment, 안쪽 this X
});
 -> ◆ 변경 ◆ 
this.setState((state, props) => ({
  counter: state.counter + props.increment
})); 
```
>State 업데이트는 병합된다
setState()를 호출할 때  
React는 제공한 객체를 현재 state로 병합
>

## 데이터는 아래로 흐른다.
부모 컴포넌트나 자식 컴포넌트 모두 특정 컴포넌트가 유상태인지 또는 무상태인지 알 수 없고  그들이 함수나 클래스로 정의되었는지에 대해서 관심을 가질 필요가 없다

## 이벤트 처리 
HTML
```
<button onclick="activateLasers()">
  Activate Lasers
</button>
```
React
```
<button onClick={activateLasers}>
  Activate Lasers
</button>
```
차이점으로, React에서는 false를 반환해도 기본 동작을 방지할 수 없습니다.  

반드시 preventDefault를 명시적으로 호출



# 11월 24일

state를 이용하여 remarkable에 변환할 마크다운 문장을 제출 <br>
글이 입력되면 handleChange 이븐트를 사용하여 state의 value를 갱신 <br>
getRawMarkup()메소드를 이용하여 init에 적용<br>
<hr>
React는 처음부터 점진적으로 적용할 수 있도록 설계되었다<br>
필요만큼 react를 사용가능<br>
codesandbox는 create-react-app으로 생성된 프로젝트와 동일한 환경에서 테스트 가능<br>
cdn방식으로 간편하게 테스트를 할 수 있도록 html코드를 제공<br>
react문서가 어렵게 느껴지면 tania rascia가 쓴 react개요를 먼저학습<br>
개발을 통해 react를 학습하고 싶다면 자습서 추천<br>
<hr>

### jsx 
jsx는 React “엘리먼트(element)” 를 생성 <br>
jsx가 필수사용은 아님 하지만 시각적으로 도움이된다고 생각 <br> 
jsx의 중괄호 안에는 유효한 모든 JavaScript 표현식을 넣을 수 있다.<br>
어트리뷰트에 따옴표를 이용해 문자열 리터럴을 정의할 수 있다<br>

<.img/> <br>
<.img> <./img> 마감을 안시켜주면 오류 발생 <br>

#### 엘리먼트 렌더링
element는 react앱의 가장 작은 단위 <br>
브라우저 DOM 엘리먼트와 달리 React 엘리먼트는 일반 객체이며(plain object) 쉽게 생성할 수 있습니다. React DOM은 React 엘리먼트와 일치하도록 DOM을 업데이트<br>
React 엘리먼트를 루트 DOM 노드에 렌더링하려면 둘 다 ReactDOM.render()로 전달<br>

### Components and Props
컴포넌트를 정의하는 가장 간단한 방법은 JavaScript 함수를 작성<br>
React가 사용자 정의 컴포넌트로 작성한 엘리먼트를 발견하면 JSX 어트리뷰트와 자식을 해당 컴포넌트에 단일 객체로 전달 이것을 Props라고 말한다<br>
props는 읽기전용<br>
<b> 모든 React 컴포넌트는 자신의 props를 다룰 때 반드시 순수 함수처럼 동작해야한다</b>

### State and Lifecycle
스스로 업데이트 = > 컴포넌트에 <b>“state”</b>를 추가 <br>




# 11월 17일

### TodoList
TodoApp과 TodoList 두개의 컴포넌트로 구성 <br>
handleChange는 모든 키보드 입력마다 React의 state를 갱신해서 보여준다 <br>
element에서 확인 <br>
시간순으로 작동하는 순서 <br>
유저입력 > habdleChange > react 의 state갱신 form element가 react state를 참조한다 <br>
유저 입력을 강제로 대문자로 변경시에도 사용 <br>
handleChange(event){
    this.setState({value:event.target.value.toUpperCase()})
}

render()에서 초기 렌더링 실행<br>
onChange()를 통해 input에 입력이됨<br>
그러므로 state 상태로 변경<br>

입력된 값은 state의 "text:"에 <b>임시로 저장</b><br>
> className처럼 html과 구분하기 위해 jsx에서 사용하는 키워드<br>

버튼 클릭시 버튼의 숫자 증가 <br>
리스트는 배열로 저장이된다 <br>
item.length를 통해 list수 확인<br>

input area에 이벤트 발생시 <br>
handleChange(e)가 동작하면서 State의 text값
변경 <br>
크롬 DevTool에서 실시간으로 state가 변화하는것을 확인
<br>
handleChange 메소드중에서 prevent
<br>
timer.html <br>
<br>
 - state = 0<br>
 - state.seconds +1 > state에 1더하기<br>
 - this.tick(), 1000  >> 1초(1000) 마다 한번씩 tick 실행<br>

#### keyprops
key는 props의 안정적으로 사용할 수 있도록 고유성을 부여<br>
유일한 값이라면 그 값이 무엇이든 상관x<br>
react가 어떤 props를 변경/추가/삭제시 식별하는것을 도움
<br>
반드시 date를 사용하지않고 배열의 index값 사용이 가능 <br> 

#### 외부 플러그인을 사용하는 컴포넌트
외부 컴포넌트를 사용한 markdown에디터 <br>
remarkable.js로 검색해야 찾을수있음 <br>

# 11월 10일 
깃허브 배포 <br>
배포전 GitHub저장소의 branch를 확인<br>
깃허브 주소를 영화 앱이 인식할 수 있도록 package.json파일을 수정<br>
(본인의 계정을 사용하면된다) <br>
homepage키와 키값을 browserslist키 아래에 추가
<br>

. push명령을 통해 최종 키 입력 <br>
. 깃허브에서 제공하는 github pages서비스로 배포 <br>
. npm install gh-pages <br>
. 마지막으로 깃허브의 저장소 이름을 <b>재확인</b> <br>
<b> git remote -v 버전 확인 </b> <br>
<b> npm run deploy </b> 입력시 배포 실행 

#### 배포
npm run build<br>
실행을 하면 build폴더 생성 > 필요한 파일 생성<br>
이 파일을 웹서버에 업로드 <br>
index.html을 살펴보면 <br>
F12 > 네이트워크 + F5(새로고침)<br>

## 파일경로 수정시 중요사항
package.json <br>
"homepage": "file:///C:/WebContentPro/movie_app_2021-5/build"
<br>
경로 설정 값을 주고 업로드해야한다 <br>
github는 github값을 넣어주고 업로드하면 실행
경로 설정 해준뒤에 <br> 
<b>npm run deploy</b>실행후 결과 창 확인 <br>
npm start로 실행해야함<br>

<hr>
React 특징 <br>
상호작용이 많은 UI개발에 적합 <br> 
컴포넌트 로직은 JavaScript로 작성 <br>
캡슐화된 컴포넌트로 개발되어 재사용이 용이 <br>
DOM과는 별개로 상태를 관리 가능 <br>
기술 스택의 나머지 부분에는 관여 X <br>
기존 코드와 별개로 개발 가능 <br> 
React Native를 이용하면 모바일 앱도 만들 수 있다. <br>
CDN:ContentDeliveryNetwork <b>or</b> <br> Content Distribution Network<br>
CORS:특정 헤더를 통해서 브라우저에게 원 출처(origin)에서 실행되고 있는 웹 애필리케이션이 다른 출처 <br>(cross-origin)에 원하는 리소스에 접근할 수 있는 권한이 있는지 없는지를 알려주는 메커니즘<br>
Babel:ECMAScript 2015+ 코드를 이전 JavaScript엔진에서 실행할 수 있는 이전 버전과 호환되는 JavaScript버전으로 변환하는 데 주로 사용되는 무료 오픈 소스 JavaScript 트랜스 컴파일러 <br>

### 간단한 컴포넌트 
React component에서 render()메소드 
<hr>

html에서 cdn에서 <.script>태그 사용시 <br> 
type = "text/babel" 추가 <br> 



# 11월 03일

Markdown Tip <br>
npm cache clean --force <br>
npm rebuild <br>
rm -rf node modules <br>
npm install <br>

rm 명령이 실행되지않을때 shell을 관리자 권한으로 실행후 다시시도
안될경우 탐색기에서 삭제
cache clean / rebuild를 통해 해결이 될때도 있음


package.json은 패키지 의존성 관리 파일
협업시 팀원딜 각자의 컴퓨터에 같은 패키지들을 설치해서 동일한 개발환경을 구성해야함
그때 사용하는것이 package.json

팀원들과의 버전이 안맞을 때 오류발생 
1. npm 버전확인 - npm -version 
2. node modoules 폴더 전체삭제
3. npm cache 삭제
4. node modules 재설치
5. npm install <br>

package.json은 version range사용
express:~4.16.1
<br>
package-lock.json은 
package.json~~~~
<br>
lock파일이 있으면 install명령은 json을 사용하지않고 실행
<br>

lock은 package.json이 변경될 때마다 업데이트가 진행된다





<hr>

# 10월 27일
###### 해결 소스 문제 방안 
npm cache clean --force <br>
npm rebuild <br>
rm -rf node_module <br>
npm install <br>

### react-router-dom 설치
터미널에서 npm install react-router-dom 입력 <br>
> components폴더에 Movie 컴포넌트 이동 <br>
> routes폴더에 Home.js & About.js 생성 <br>
> Home.js수정 <br>
> Home.css 생성 <br>
> App.js 수정 <br>

localhost:3000/#에 path props로 전달한 값
/about을 붙인후 접속하면<br> 
URL: localhost:3000/#/about
<br>

path props 를 "/"로 입력한 이유 <br>
localhost:3000접속시 기본으로 보여줄 컴포넌트를
Home으로 하기위해서<br>

localhost:3000접속시 주소 뒤에 자동으로 /#/ 붙으면서 영화 앱 화면 표시 <br>

리다이렉트 기능 사용 -> route props의 history키를 활용 해야함 <br>

history키에는 push, go, goBack, goForward와 같은 키가 있으며, 그 키에는 URL을 변경해 주는
함수<br>

이 함수들을 이용해서 리다이렉트 기능을 구현<br>

#### App.js 해결방안 
Route 컴포넌트에 exact props를 추가하면 해결 <br>
exact props는 Route 컴포넌트가 path props와 정확하게 일치하는 URL에만 반응하도록 한다

# 10월 13일
import Movie from './Movie' <br>
key props는 유일해야 한다 API에서 넘겨주는 id값을 사용
console.log()는 사용 X

### Movie 컴포넌트 수정하기
console을 확인해 보면 두가지 warnin을 확인가능하다<br>
JSX에 사용한 속성 중 class속성이 className으로 사용되어야 한다 <br>
genres props가 required로 되어 있는데 
Movie 컴포넌트에 undefined로 넘어감 <br>
<hr>
Slice함수를 이용하여 구현<br>
"hereisstring".slice(0,10) <br>
└012 ... 11┘       시작,끝 <br>
hereisstri <br>
└012 ... 9┘ 
<br>
genres.map((genre,index)=> {...}) <br>
            배열 원소 / 1,2,3, ... 번째

## ★ Code 해석 ★
function Movie ({id,title,year,summary,poster}){<br>
    retrun<.h4>{title}<.h4> <br>
}<br>
└ 음식 앱을 만들 때 컴포넌트를 map() 함수로 출력했던 것과 같이 코딩

import Movie from './Movie' <br>
└ movies.map()에 전달한 함수가 <Movie/>를 반환하도록 지정 

<Movie <br>
id={movie.id} <br>
year={movie.year} <br>
title={movie.title} <br>
summary={movie.summary} <br>
poster={movie.medium_cover_image} <br>
/> <br>
└ key props는 유일해야한다 그러므로 API에서 넘겨주는 id값을 사용해야한다

# 10월 06일
### 영화 앱 만들기
영화 데이터를 로딩시 fetch()함수를 이용한다 <br>
첫번째 인자로 URL, 두번째 인자로 옵션 객체를 받고, Promise 타입의 객체를 반환<br>
하지만 <b>※ axios ※</b> 를사용 <br>

>터미널에서 "npm install axios" 설치

status : 응답상태 메시지 <br>
data : 영화 데이터<br>
movie_count : API가 보내준 영화 데이터 개수<br>
limit : 보내준 데이터의 개수<br>
movies키의 서브키로 id,url,lmdb_code,title 등 제공한다<br>
> ※ YTS에서는 영화 토렌트 파일을 업로드 하기에 불법이라서 주소가 매번 바뀐다.

> ※ YTS의 endpoint/list_movies.json사용시
yts-proxy.now.sh에 /list_movies.json을 붙이면 사용가능 <br>
● YTS의 다른 endpoint와 함께 사용시 <br>
yts-proxy.now.sh에 endpoint를 붙이면 가능

## [ EX ]
● yts-proxy.now.sh/list_movies.json?movie_id=10 이하고 접속하면 아이디가 10인 영화의 자세
한 정보를 볼 수 있다 <br>

● API를 사용하려면 axios를 import한 다음, componentDidMount()함수에서 axios로 API를 호출 <br>

● getMovies()함수를 만들고, 이 함수 안에서 axios.get()이 실행<br>

● axios.get()의 return값은 movies에 저장<br>
● componentDidMount()함수가 실행되면 this.getMovie()가 실행<br>

● 시간이 필요하다는 것을 알리기 위해서는 async, await 키워드가 필요<br>

● 자바스크립트에게 시간이 필요하다는 것을 알리려면 async를 ()앞에 붙이고,<br>
● 실제 시간이 필요한 대상인 axios.get()함수 에는 await을 붙인다

#### 이 데이터 구조는 음식 앱을 만들 때 사용했던 데이터 구조와 동일 !!

# 09월 29일
 git --version => 버전확인후 2.28.0이상 버전 설치 권장<br>
 git config --global init.defaultBranch main<br>
 git branch -m master main<br>
<br>
git clone http://github~~ <br>
cd {repo-name} -[로컬 프로젝트로 폴더로 들어감] <br>
npm install - [이때 node-module 설치] <br>
npm start <br>

npm install prop-types 설치<br>
import PropTypes (<-이름 변경가능) from 'prop-types'; 추가 App.js파일 위에 <br>

prop-types 설치 -> 등록이 되어있으면 설치가 정상적으로 된것. <br>

isRequired는 필요하다는 의미 - rating에는 string 자료형이 반드시 <b><u>필요</u></b>! <br>
rating:PropTypes.<b><u>string.</u></b>isRequired -> <b><u>number</u></b> 교체 <br>


* props - 정적인 데이터만 가능 <br>
* state - 동적인 데이터를 다룰때 사용 <br>
└─> class형 컴포넌트에서 사용 <br>

<mark>JSX</mark>를 반환해야 하지만 class형에서는 바로 return을 사용할 수 없다.<br>
render() 함수 내에서 return문을 사용 <br>
함수형 컴포넌트는 return문이 <mark>JSX</mark>를 반환하지만 <br>
클래스형 컴포넌트는 render()함수가<mark>JSX</mark>를반환 <br>

#### state 정의
class 안에 state = {} 작성후 state를 정의<br>
* state는 객체형태의 데이터 <br>
* state사용시  소문자로 사용한다 <br>
* state = count키와 키값을 0으로 추가 <br>
<ul>
state={ <br>
    count:0 <br>
} <br>
</ul>
<hr>
<ul>
add = () => { <br>
    console.log('add'); <br>
}<br>
minus = () => { <br>
    console.log('minus'); <br>
}<br>
<.button onClick =this.add}>ADD</button> <br>
<.button onClick =this.minus}>Minus</button><br>
this.state.count = 1 <br>
this.state.count = -1 <br>
└─> ※ <b>경고</b> 발생 state는 직접 변경 XX <br>

### 변경 >> this.setState({count:1}) OR<br>  this.setState({count:-1}) 
<b> setState()</b> 함수를 사용해서 state값을 변경 <br>
-> 경고는 없어지지만 단순히 버튼실행시 1/-1로만 변할뿐 지속적인 증가는 XX
- 증감키 : this.setState({count:this.state.count + 1 / -1}) <br>
- └─ 성능에 문제가 생길수있다
- setState()함수의 인자로 전달시 성능 문제 X
this.setState(current=>({count:this.state.count +1/-1}))
</ul>

constructor() : 컴포넌트 생성시 state 값을 초기화 or 메서드를 바인딩 할 때 사용 <br>

자바스크립트에서<mark>super</mark>는 부모클래스 생성자의 참조한다는 의미<br>
super를 호출하기 전에는 this를 사용할수없다 <br>
└─super를 먼저 호출후 this를 사용이 가능하다 <br>





# 09월 17일 
컴포넌트는 자바스크립트와 HTML을 조합한 JSX라는 문법을 사용해서 만든다. <br>

import React from 'react' 
### props
Props란 컴포넌트에서 컴포넌트로 전달하는 데이터를 말한다. <br>
함수의 매개변수 역할을 하는 것 <br> 
props를 사용하면 컴포넌트를 효율적으로 사용할 수 있다.<br>
<hr>
>단순히 붙여 놓기만 했을 경우 문제발생 <br>
리스트의 내용이 모두 동일 <br>
만약 영화 앱의 리스트라면 값이 모두 달라야하는데 이때 사용하는것이 <b>props</b> <br>
props의 전달 데이터는 <b> 문자열인 경우를 제외하면 모두 중괄호 ‘{ } ‘로 감싸야 한다.</b> <br>
props에는 불리언 값(true, false), 숫자, 배열과 같은 다양한 형태의 데이터를 사용할 수 있다.<br>
객체의 특정 값을 사용할 때는 점(.)연산자를 사용한다<br>
데이터의 개수가 많아지면 구조 분할 할당을 사용하는 것이 편리<br>

### key props 
리스트의 각 원소는 유일한 “key” prop을 가져야 함 <br>
리액트의 원소들은 유일해야 하는데 리액트 원소가 리스트에 포함되면서, 유일성이 없어져서 발생하는 문제 <br>
img 관련 메시지는 alt속성을 추가 하지 않아서 생기는 것이니 alt 속성을 추가하면 해결 할 수 있다 <br>
이미지의 위치는 /src/images/1.jpg이다. 반드시 src 아래 두어야 한다 <br>
ex > import img01 from ‘./images/1.jpg’ <br>

# 09월 08일 
리액트 기초개념

npm install 
npx -g

npx create-react-app movie_app_2021-5<br>

Edit.package.json<br>
test,eject삭제

npm start로 앱을 실행

App.js <br>
index.js<br>
해석하고 <br>
index,html 에 끼워 넣는 형식 <br>




# 09월 01일
<br>
https://2020.stateofjs.com/ko-KR/
<br>
var . boolean . string . for/if/while<br>
let . const
<br>
power shell 관리자권한으로 실행 (코드 붙여 넣고 껏다 키기)<br>
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('[https://community.chocolatey.org/install.ps1](https://community.chocolatey.org/install.ps1)'))
<br>
choco -v 로 버전확인

내용<br>
클론 코딩 : 실제로 존재하는 사이트나 앱의 코드를 보며 그대로 따라 만들면서 해당 언어나 <br>
기술을 습득하는 방법<br>
<br>
완성된 프로젝트를 클론해서 하나씩 완성해 가는 실습위주의 학습으로 <br>
3가지 : 빠르고,효과적,실용적 <br>
GitHub의 수많은 오픈 소스들이 학습의 도구가 된다. <br>
<hr>
부작용 및 학습방법<br>
1.맹목적으로 카피해서 사용 X<br>
2.모르는 내용 코드 -> 질문 or 검색<br>
3.학습자의 개성을 살려 코딩<br>
4.주석을 상세하게<br>
5.readme.md를 이용해 문서화<br>
6.지속적인 커밋 포트폴리오 생성<br>
7.학습한 내용으로 다른 프로젝트를 자체적으로 생성