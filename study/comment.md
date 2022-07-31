# comment

### fetch()를 이용해서 데이터 보내기
- fetch() request에 포함할 수 있는 또 다른 선택적 속성은 body.
- body 속성은 HTTP(또는 API) request의 일부로, 보내려는 모든 데이터를 포함할 수 있음.
- API request를 할 때, 데이터가 포함된 헤더와 함께 전송됨.
- fetch()를 사용하여 데이터를 보낼 때 보낸 데이터가 JSON인지 쿼리 문자열인지 API에 알려주는 Content-type을 지정해야 함.
https://gomakethings.com/how-to-send-data-to-an-api-with-the-vanilla-js-fetch-method/

### fetch()를 이용해서 JSON객체 보내기
https://gomakethings.com/how-to-send-data-to-an-api-with-the-vanilla-js-fetch-method/#sending-data-as-a-json-object

## 미들웨어
### express.text([options])
- Express에 내장된 미들웨어 기능.
- body-parser를 기반으로 request payload로 전달한 문자열을 파싱함.
https://expressjs.com/ko/api.html#express.text

### express.json([options])
- Express에 내장된 미들웨어 기능.
- body-parser를 기반으로 request payload로 전달한 JSON을 파싱함.
- 문자열을 받아서 json으로 바꿔줌.
- 주의할 점은 `express.json()`은 `header`에 `Content-Type`이 `express.json()`의 기본 값인 `"application/json"`과 일치하는 request만 보는 미들웨어를 반환함.
- 다시 말해, `headers: { "Content-type": "application/json" }`인 request만 `express.json()`을 실행함.
https://expressjs.com/ko/api.html#express.json

## <a href="https://developer.mozilla.org/ko/docs/Web/HTTP/Status">HTTP 상태 코드</a>
### 200 OK
요청이 성공적으로 되었습니다.

### 201 Created
요청이 성공적이었으며 그 결과로 새로운 리소스가 생성되었습니다. 이 응답은 일반적으로 POST 요청 또는 일부 PUT 요청 이후에 따라옵니다.

### 400 Bad Request
이 응답은 잘못된 문법으로 인하여 서버가 요청을 이해할 수 없음을 의미합니다.

### 404 Not Found
서버는 요청받은 리소스를 찾을 수 없습니다. 브라우저에서는 알려지지 않은 URL을 의미합니다.



-----

#### `id`, `_id` 헷갈림
- `_id`는 DB에서 나오는 Mongo에 의해 생성됩니다.
- `id`는 HTML 요소가 가지고 있는 것입니다.



