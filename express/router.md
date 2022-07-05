
## Router
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
