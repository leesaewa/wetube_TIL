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
- `/` --> 서버의 root.
