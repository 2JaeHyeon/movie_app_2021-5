# 이재현 201840223
<hr>
※ 첫 글자 사용시 대문자 사용<br>
function으로 정의 내린 것을 (컴포넌트)라고 칭한다<br>
컴포넌트는 자바스크립트와 HTML을 조합한 JSX라는 문법을 이용<br>
JSX의 문법은 JS와 HTML문법의 조합한 것<br>

# 10월 27일

npm cache clean --force
npm rebuild
rm -rf node_module

### react-router-dom 설치
터미널에서 npm install react-router-dom 입력 <br>
> components폴더에 Movie 컴포넌트 이동 <br>
> routes폴더에 Home.js & About.js 생성 <br>
> Home.js수정 <br>
> Home.css 생성 <br>
> App.js 수정 <br>

path props 를 "/"로 입력한 이유 <br>
localhost:3000접속시 기본으로 보여줄 컴포넌트를
Home으로 하기위해서<br>

localhost:3000접속시 주소 뒤에 자동으로 /#/ 붙으면서 영화 앱 화면 표시 <br>

리다이렉트 기능 사용 -> route props의 history키를 활용 해야함 <br>

history키에는 push, go, goBack, goForward와 같은 키가 있으며, 그 키에는 URL을 변경해 주는
함수<br>

이 함수들을 이용해서 리다이렉트 기능을 구현<br>



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