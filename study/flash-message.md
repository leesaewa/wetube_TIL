# <a href="https://www.npmjs.com/package/express-flash">express-flash</a>
- `$ npm i express-flash`
- 사용자에게 `flash message`를 남길 수 있게 해줌.
  - 템플릿에 사용자에게 메시지를 남길 수 있게 해주는 미들웨어.
- `session`에 근거하기 때문에 한 사용자만 볼 수 있음.
- `req.flash("error", "Not authorized");`
  - 미들웨어에 메시지의 타입과 내용을 입력.
