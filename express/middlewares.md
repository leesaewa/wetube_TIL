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
