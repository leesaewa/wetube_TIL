# heroku err

# SCSS찾을 수 없음
- <a href="https://dashboard.heroku.com/apps/18fdaa63-a383-4fd1-8d1f-a725f77320f0/activity/builds/e62dcefb-e4cc-4ef3-a8ce-1b516ac6fdf2">에러 내역</a>
```
Error: Module build failed (from ./node_modules/sass-loader/dist/cjs.js):
SassError: Can't find stylesheet to import.
 ╷
7 │ @import "./Components/common.scss";
 │         ^^^^^^^^^^^^^^^^^^^^^^^^
 ```
 - 개빡치게 이런 에러가 자꾸 뜨는거임.... 구글링을 해봤더니 소용이 없었음.
 - 내가 해본 것
  - 경로 문제인가 싶어서 `./`를 `/`로 하거나 `/`를 없앰. -> 실패
  - SCSS loader의 문제인 건가 싶어서 다운그레이드 함. -> 실패
  - 그래서 자세히 살펴보니 `./Components`의 `C`가 대문자네? 폴더명은 대문자가 아니라 소문자임... 설마, 이건가 싶어서 `c`소문자로 바꿔줌. -> 성공
  - 와... 4시간 버림.....ㅎㅎ

