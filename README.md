# wetube_TIL

코드는 따로 올렸음.
<a href="https://github.com/leesaewa/wetube-reloaded">코드는 이쪽으로</a>

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
