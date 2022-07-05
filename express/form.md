## post
``form(method="POST")``
- 기본은 get인데 get은 구글이나 네이버에서 검색할 때 주로 사용함. (데이터를 받는 게 목적)
- post방식은 파일을 보내거나, database에 있는 값을 바꿀 때, 로그인할 때 사용

## urlencoded
- express에 내장된 미들웨어 기능.
- express는 기본적으로 form을 처리하지 못함.
- 옵션 중에서 ``extended``는 body에 있는 정보들을 js의 object로 보기 좋게 보여줌.
  - ``true``가 기본값.
- route를 사용하기 전에 선언해줘야 함.

``app.use(express.urlencoded({ extended: true }));``
-> 너의 express application이 form의 value들을 이해할 수 있도록 하고, 우리가 쓸 수 있는 자바스크립트 형식으로 변형시켜줄 거임.

## req.body
- form을 통해 submit된 데이터의 키-값 쌍을 포함함. (주로 POST로 유저의 정보 또는 파일 업로드를 보냈을 때 )
- 기본적으로는 undefined.
- express.json(), express.urlencoded()와 같은 미들웨어를 사용해야 함.
