<h3 align="center">Back-end study</h3>

<p align="center">
  <img src="https://img.shields.io/badge/Server-black" />
  <img src="https://img.shields.io/badge/Nodejs-green" />
  <img src="https://img.shields.io/badge/Express-purple" />
  <img src="https://img.shields.io/badge/Visual Studio Code-blue" />
</p>

> 📌  personal study Repo
>
> 🗂  Reference: 생활코딩, 26th Server seminar 자료, Node.js 공식 홈페이지

<br/>

<!-- Contents -->

<h2>Contents</h2>

- [Overview](#overview)
- [Javascript](#javascript)
- [JSON](#json)
- [Node.js](#nodejs)
- [Flow Control](#flowcontrol)
- [Module](#module)
- [Express](#express)

<br/>

<!-- overview -->

<h2>Overview</h2>
📱  Client : **서비스 요청자** -> 서비스를 사용하는 사용자

🗄  Server :  **서비스 자원의 제공자** -> 네트워크를 통해 클라이언트에게 서비스 및 정보를 제공, 다른 서버에 요청 보내기도 함

<br/>

<!-- javascript -->

## Javascript 

- 코드를 한 줄씩 번역하고 실행 
- 실행속도가 컴파일 언어에 비해 느림
- 타입을 명시하지 않음
- 프로토타입 기반의 객체 지향 언어

<br>

**Hoisting**

- 변수의 정의가 그 범위에 따라 **선언**과 **할당**으로 분리되는 것

> 작성자 코드

```javascript
function hoisting(){
	console.log(x);
	var x = 'abc'
	console.log(x)
}
```

> Javascript 엔진에서 호이스팅 된 코드

```javascript
function hoisting(){
	var x
	console.log(x)
	x = 'abc'
	console.log(x)
}
```

<br>

**Data Type**

- ***[Primitive Type]***
  - Boolean
  - Number
  - String
  - Symbol
  - Null
  - Undefined

- ***[Object Type]***
  - Object

<br>

**Object**

- Array
  - 객체 타입
  - arr_name = [a, b, c] 형태
- Function
  - 객체 타입
  - 하나의 특별한 목적의 작업을 수행하도록 설계된 독립적인 블록
  - **일급 객체**
    - 변수, 데이터 구조에 담을 수 있다
    - 다른 함수의 파라미터로 사용 가능
    - 반환 값으로 사용 가능
    - 런타임 시 생성 가능

> 함수 선언식 vs 함수 표현식
>
> ❗️함수 선언식은 기존 다른 언어와 비슷한 함수 선언 구조인데, JS에서는 화살표 함수(함수 표현식)를 사용하는 것 같다.

<br/>

<!-- json -->

## JSON

**Javascript Object Notation**

- 자바 스크립트 객체 표현식
- **Name : Value** 로 구성된 프로퍼티(property)의 정렬되지 않은 집합
- 프로퍼티 값으로 **함수**가 올 수도 있는데, 이러한 프로퍼티를 **메소드**라고 한다.
- 클라이언트와 통신 시 주로사용
  - -application/json

> JSON 객체

``` javascript
var 객체이름 = {
	key1: value1,
	key2: value2,
}
```

> JSON 배열

```javascript
var 객체이름 = [
	{
		key1: value1, 
		key2: value2
	},
	{
		key1: value3, 
		key2: value4
	}
]
```

❗️가끔 json 객체와 배열이 헷갈릴 때가 있다...

<br/>

<!--nodejs-->

## Node.js

- 자바스크립트 기반 서버 플랫폼
- 이벤트 기반
- 싱글 스레드 기반
- non-blocking I/O
- 비동기 방식

> 프로그램 언어  ❌
>
> 프레임워크  ❌
>
> **자바스크립트를 실행시키는 *런타임 환경***  ⭕️

<br>

**Express**

- NodeJS 기반의 웹 어플리케이션 ***프레임 워크***
- 서버를 구축하기 쉽게 틀을 제공

<br>

**Event-Driven**

- 이벤트가 발생할 때, 미리 지정해둔 작업을 수행하는 방식

![스크린샷 2020-09-02 오후 10 04 54](https://user-images.githubusercontent.com/56633607/91986986-6380f980-ed68-11ea-9d87-4efc0e0e5b6e.png)

> 출처 : Node.js 공식 홈페이지

<br/>

<!--flowcontrol-->

## Flow Control (흐름 제어)

***Blocking & Non-Blocking?***

### Blocking (동기)

- 요청을 하고 완료를 할 때 까지 기다리는 방식
- 백그라운드 작업 완료 여부를 계속 확인

### Non-Blocking (비동기)

- I/O 작업이 진행되는 동안 작업이 멈추지 않고 다음 작업 수행
- **요청을 하고 바로 제어권을 돌려 받는 방식**

> Blocking

```javascript
var fs = require("fs");
var data = fs.readFileSync('input.txt');

console.log(data.toString());
console.log("Program Ended");		
```

> result

```
this is a sample text
Program Ended
```

<br/>

> Non-Blocking

```javascript
var fs = require("fs");

fs.readFile('input.txt', function (err, data) {
   if (err) return console.error(err);
   console.log(data.toString());
});

console.log("Program Ended");
```

> result

``` 
Program Ended
this is a sample text
```

<br>

<h3>Promise</h3>

- ES6부터 공식적으로 포함된 흐름 제어 패턴
- 내부적 예외처리 구조

> Fulfilled (이행)

```javascript
new Promise(function(resolve, reject) {
	resolve();
})
```

> Rejected (실패)

```javascript
new Promise(function(resolve, reject){	
	reject();
})
```

<br>

> practice

```javascript
let isMomHappy = false;
let phone = {
    brand: 'Samsung',
    color: 'black'
}

var willIGetNewPhone = new Promise((resolve, reject) => {
    if(isMomHappy){
        resolve(console.log(phone));
    }else{
        //reject(console.error());
        reject(console.log(new Error('Mom is not happy')))
    }
})
```

<br>

### Async

- ES7부터 지원하는 자바스크립트 비동기 패턴
- 장황한 **promise** 코드를 한번 더 깔끔하게 줄여줌
- 동기 코드와 매---우 유사함

> Async

- promise를 사용하지 않고도 효과적으로 콜백헬 해결
- **async는 암묵적으로 promise를 반환**

> Await

- promise를 기다림 (성공 or 실패)
- async로 정의된 내부에서만 사용 가능

<br>

<!--module-->

## Module

- 독립된 기능을 하는 함수나 변수들의 집합
- 모듈 자체가 하나의 프로그램이면서 다른 프로그램의 **부품**으로 사용할 수 있음
- 재사용에 용이함
- Node에서는 각 파일을 모듈화, **1파일 = 1모듈**

### crypto

- **문자열을 암호화, 복호화, 해싱하는 모듈**
- 복호화할 수 없는 암호화 방식
- 비밀번호 암호화에 주로 사용
- 주로 해시 기법을 사용

> Example

```javascript
const crypto = require('crypto')
crypto.pbkdf2('secret', 'salt', 100000, 64, 'sha512', (err, derivedKey) => {
	if(err) throw err;
	console.log(derivedKey.toString('hex'));	
})
```

### File System Module

- 파일 생성, 삭제, 읽기, 쓰기
- 폴더 생성, 삭제

> 비동기 방식
>
> > fs.readFile() 
> >
> > fs.writeFile()

> 동기 방식
>
> > fs.readFileSync() 
> >
> > fs.writeFileSync()

<br>

<!--express-->

## Express

- Node를 위한 빠르고 간결한 웹 프레임워크
- HTTP 요청에 대해 라우팅 및 미들웨어 기능 제공

> 1. Express 설치

```
npm install express -g
```

> 2. 폴더 정해서 express 프로젝트 생성기 생성

```
npm install -g express-generator
```

>3. express 프로젝트 생성

```
express [project name]
```

> 4. 코드 작성 후 터미널에서

```
npm install
```

``` 
npm start
```

> 5. localhost:3000 접속 후 Express 뜨면 성공

### Routing

- URI 및 특정한 HTTP 요청 메소드 (GET, POST 등) 인 특정 엔드포인트에 대한 클라이언트 요청에 애플리케이션이 응답하는 방법을 결정
- 한 파일에 모든 라우팅을 관리하는건 지양한다