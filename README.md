# wetube_TIL

코드는 따로 올렸음.
<a href="https://github.com/leesaewa/wetube-reloaded">코드는 이쪽으로</a>

## 220703 TIL

#### Array database (가짜 데이터베이스로 샘플 비디오 만들기)

##### array database와 HTML 상호작용 과정
1. 각 비디오에 id 부여
2. id를 기반으로 비디오마다 anchor 생성
3. 임의의 id를 가진 url에 접근하려고 할 때, 해당 id를 가져와서 변수에 저장
4. 저장된 id를 기반으로 해당 id 에 해당하는 object를 변수에 저장
5. 저장된 object를 기반으로 HTML 렌더링하여 contents 출력

```const { id } = req.params;
const id = req.params.id;```

##### 링크에 변수를 담는 법
- 대상: href, class, id
1. ``a(href=`/videos/${video.id}`)=video.title``
2. ``a(href="/videos/" + video.id)=video.title``

##### ternary operator
- 만약 조회수가 ``1``일 때, ``views``가 아닌 ``view``가 출력되도록 함.
  ``h3 #{video.views} #{video.views === 1 ? "view" : "views"}`` inline if문
  -> 만약 video.views가 1과 같다면 'view'를, 같지 않다면 'views'를 보여줌.

##### post
``form(method="POST")``
- 기본은 get인데 get은 구글이나 네이버에서 검색할 때 주로 사용함. (데이터를 받는 게 목적)
- post방식은 파일을 보내거나, database에 있는 값을 바꿀 때, 로그인할 때 사용

##### urlencoded
- express에 내장된 미들웨어 기능.
- express는 기본적으로 form을 처리하지 못함.
- 옵션 중에서 ``extended``는 body에 있는 정보들을 js의 object로 보기 좋게 보여줌.
  - ``true``가 기본값.
- route를 사용하기 전에 선언해줘야 함.

``app.use(express.urlencoded({ extended: true }));``
-> 너의 express application이 form의 value들을 이해할 수 있도록 하고, 우리가 쓸 수 있는 자바스크립트 형식으로 변형시켜줄 거임.

###### req.body
- form을 통해 submit된 데이터의 키-값 쌍을 포함함. (주로 POST로 유저의 정보 또는 파일 업로드를 보냈을 때 )
- 기본적으로는 undefined.
- express.json(), express.urlencoded()와 같은 미들웨어를 사용해야 함.




-------

## 220702 TIL

#### pug
- Haml의 영향을 많이 받은, Node.js 및 브라우저용 JavaScript로 구현된 고성능 템플릿 엔진
- ``npm i pug``
- 어떤 자바스크립트 코드라도 넣을 수 있음.

##### partial
- 반복작업을 따로 만들어서 include할 수 있음!!! 이게 강점임. it was cool
- ``include partials/footer``

##### inheritance(상속) / extends(확장)
```
doctype html 
html(lang="ko")
  head
    title #{pageTitle} | Wetube

  body 
    block content
  include partials/footer
  ```

- 베이스를 만들어서 그 베이스를 기준으로 확장시켜 가는 것.
- 베이스 안에 block이나 variable을 만들 수 있음.
###### block
  - block = ``extends base``
###### 변수
  - 변수는 #{}로 작성해야 함.
  - 변수만 작성하고 싶을 경우에는 이렇게 함. (변수와 텍스트를 섞어쓰지 않을 경우)
    - ``h1=pageTitle``
  - ``res.render("home", {pageTitle: "Home"}``
  - render는 2개의 argument를 받음. 하나는 ``view``, 다른 하나는 ``템플릿에 보낼 변수(pug)``

##### conditionals
```
if fakeUser.loggedIn
            li 
              a(href="/logout") Log Out
          else
            li 
              a(href="/login") Login
```
- JS의 if문과 똑같음.

##### iteration
- 반복. each A in B = array B에있는것들을 A에 반복하여 나열.
- Pug는 each와 while라는 두 가지 기본 반복 방법을 지원함.
```
ul
each val in [1, 2, 3, 4, 5]
li= val
```
- 배열이나 객체에 반복할 값이 없으면 실행될 else 블록을 추가할 수도 있음.
  - 이 때 else는 js가 아님. 
```
- var values = [];
ul
each val in values
li= val
else
li There are no values
```

- array설정해주기
- array 넣을 템플릿에 가서
  each video(anything whatever you want) in videos(videoController에서 설정해준 array)
  li=video(same thing value before videoController에서 설정해준 array)


##### mixin
- scss랑 비슷한 역할인듯.
- html 코드를 재사용할 수 있게 해줌.
- partial이긴 하지만 데이터를 받을 수 있는 똑똑한 partial을 의미함.

```
-controller-
const videos = [
{
title: "First Video",
rating: 5,
comments: 2,
createdAt: "2 minutes ago",
views: 62,
id: 1,
}
]

-mixin-
mixin video(info)
div
h4=info.title
ul
li #{info.rating}/5.
li #{info.comments}/comments.
li Posted #{info.created}.
li #{info.views} views.

-pug-
include mixins/video

each info in videos
+video(info)
```



#### html 적용하는 법
- pug라는 view engine을 쓴다. (템플릿 엔진)
- 템플릿 엔진을 렌더링하기 위해 다음과 같은 어플리케이션 설정이 필요함.
  - server.js에 ``app.set("view engine", "pug");`` 설정하고, 
  - home(index)에 보여질 함수(controller) 안에 ``res.render("home")``로 express에 설정함
  - 예) ``export const trending = (req, res) => res.render("home");``



------

## 220630 TIL

#### morgan
- HTTP request logger middleware for node.js
- morgan 패키지는 node.js 서버로 구성된 웹 환경에서 HTTP request 로그를 관리하기 위한 미들웨어이다.
- 좀 더 정교함. GET, path, status code 정보를 가지고 있음.

##### combined
Standard Apache combined log output.
시간, method, http버전, 사용중인 브라우저, os알려줌
``:remote-addr - :remote-user [:date[clf]] ":method :url HTTP/:http-version" :status :res[content-length] ":referrer" ":user-agent"``

##### common
Standard Apache common log output.
``:remote-addr - :remote-user [:date[clf]] ":method :url HTTP/:http-version" :status :res[content-length]``

##### dev
Concise output colored by response status for development use. The :status token will be colored green for success codes, red for server error codes, yellow for client error codes, cyan for redirection codes, and uncolored for information codes.
``:method :url :status :response-time ms - :res[content-length]``

##### short
Shorter than default, also including response time.
``:remote-addr :remote-user :method :url HTTP/:http-version :status :res[content-length] - :response-time ms``

##### tiny
The minimal output.
``:method :url :status :res[content-length] - :response-time ms``

#### Router
```
const globalRouter = express.Router();
const userRouter = express.Router();
const videoRouter = express.Router();

app.use("/", globalRouter);
app.use("/videos", videoRouter);
app.use("/users", userRouter);
```
- 컨트롤러와 url의 관리를 쉽게 해줌.
- url을 그룹화 해줌. 도메인. ``/users/edit/inde.html~~~``
- 라우터와 컨트롤러(function)를 섞어서 쓰는 건 좋지 않음. 파일을 나누는 걸 추천.

##### js 나눠서 express server.js에 익스포트, 임포트하기
1. export default
- ``export default globalRouter;``
- 파일 당 한가지의 default export만 가질 수 있음. 두 개는 안 됨.
- server.js에 ``import globalRouter from "./routers/globalRouter";`` 임포트
- 임포트할 때, default 변수명을 그대로 가져오지 않고 변경을 해도 됨. 왜냐하면 default는 하나밖에 못 쓰기 때문.
  하지만 같은 이름을 유지하는 게 좋음.

2. export
- export : 여러 개를 익스포트할 수 있음.
  ``export const trending = (req, res) => res.send("home page videos");``
- 여러개를 임포트할 경우, ``import { trending } from "../controllers/videoController";``로 함.
- 임포트할 때 선언한 변수명을 그대로 가지고 와야 함. 변경하면 안됨. default와의 차이점.


#### URL parameters
``videoRouter.get("/:id", see);``
- ex)) ~~/lectures/숫자(변수)
- ``:id``의 ``id``는 변경돼도 상관없으나 꼭 ``:``를 정의해야 함.
- 자동으로 라우터 생성. url에 변수를 넣을 수 있게 해줌.
- ``:id``는 제일 아래에 써주는 게 좋음.
  - 만약 ``/upload``라는 라우터가 중간에 있다면 ``~~/lectures/upload``페이지가 아닌 ``:id`` 변수로 인식해버림.
  - 정규식으로 숫자만 나오게 하면 상관없음.
  
#### 정규식
- 문자열로부터 특정 정보를 추출해내는 방법.
- ``(\\d+)`` -> 숫자만 나오게 함.





-------

## 220629 TIL

#### middlewares
```
const logger = (req, res, next) => {
  console.log(`${req.method} ${req.url}`);
  next();
};

const privateMiddleware = (req, res, next) => {
  const url = req.url;
  if (url === "/protected") {
    return res.send("<h1>not allowed</h1>");
  }
  console.log("allowed");
  next();
};
```

- 중간에 있는 소프트웨어.
- 응답하는 함수가 아니라 작업을 다음 함수에게 넘김.
- next함수를 호출해야만 middleware인 걸 알 수 있음.
- 모든 callback function = controller middleware가 될 수 있음.
- next()함수는 middleware에 해당하는 함수의 다음 함수를 실행시킴.
- middleware는 request에 응답하지 않음. request를 지속해줌.

#### app.use
```
app.use(gossipMiddleware);
app.get("/", handleHome);
```
- 순서가 중요함. use다음이 get
- global mmiddleware를 만들 수 있게 해주는 것. 모든 route에서 사용할 수 있음.


------

## 220628 TIL

### express설정

```
import express from "express";

const PORT = 4000;

const app = express(); //create express application

//get response
//req, res의 이름은 마음대로 지어도 됨. 하지만 반드시 두 개의 arguments가 필요
app.get("/", (req, res) => {
  return res.send("<h1>i still love you.</h1>");
});

//외부 접속
const handleListening = () =>
  console.log(`server listening on port http://localhost:${PORT}/`);

app.listen(PORT, handleListening);
```

#### root
- / --> 서버의 root.

#### get
` app.get(path, callback) `
- HTTP method.
- 지정된 콜백 함수를 사용하여 HTTP GET요청을 지정된 경로로 라우팅.
- request object, response object. 브라우저에게 request를 받으면 꼭 response해줘야 함. -> 안 그러면 빙글빙글 무한 로딩.

#### request
- req객체는 http request를 나타내며 요청 query string, parameters, body, HTTP headeers 등에 대한 속성을 가짐.

#### response
- res 객체는 express 앱이 HTTP request를 받을 때 보내는 HTTP response를 나타냄
- response해주는 방법은 두가지가 있음.
`res.end, res.send`
