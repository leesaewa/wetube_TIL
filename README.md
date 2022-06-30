# wetube_TIL

코드는 따로 올렸음.
<a href="https://github.com/leesaewa/wetube-reloaded">코드는 이쪽으로</a>

## 220630

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

## 220629

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

## 220628_ express설정

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
