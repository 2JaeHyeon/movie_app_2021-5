# 이재현 201840223
<hr>
※ 첫 글자 사용시 대문자 사용<br>
function으로 정의 내린 것을 (컴포넌트)라고 칭한다<br>
컴포넌트는 자바스크립트와 HTML을 조합한 JSX라는 문법을 이용<br>
JSX의 문법은 JS와 HTML문법의 조합한 것<br>

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