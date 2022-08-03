# express로 이미지(img태그) 업로드 하기
> <a href="https://bitkunst.tistory.com/entry/Nodejs-express-4-%EC%A0%95%EC%A0%81%EC%9D%B8-%ED%8C%8C%EC%9D%BC-%EC%B2%98%EB%A6%AC%ED%95%98%EA%B8%B0">참고 페이지</a>

## 요약
- `server.js`에 아래 코드를 입력
- `app.use("/", express.static("./src/client/img"));`
  -`express.static( )`은 정적인 파일들을 가져오는 미들웨어
  - `app.use("경로", express.static("정적인 파일들이 위치할 디렉토리"));`
- 이런 식으로 웹팩을 사용하지 않아도 `css`, `js`도 넣을 수 있음.
- `img(src="/logo.png")`처럼 적용시킴.
- 참고로 css에 img를 적용하고 싶을 때는, `background-image: url("/src/client/img/background.jpg");` 전체 경로를 적었더니 적용이 됐다.
  왜 그러는지는 아직 완벽하게 이해가 안 됐다... 하여튼 html처럼 쓰면 에러 뜸.
