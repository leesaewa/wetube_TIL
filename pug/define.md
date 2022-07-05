## pug

- Haml의 영향을 많이 받은, Node.js 및 브라우저용 JavaScript로 구현된 고성능 템플릿 엔진
- `npm i pug`
- 어떤 자바스크립트 코드라도 넣을 수 있음.

## html 적용하는 법
- pug라는 view engine을 쓴다. (템플릿 엔진)
- 템플릿 엔진을 렌더링하기 위해 다음과 같은 어플리케이션 설정이 필요함.
  - server.js에 ``app.set("view engine", "pug");`` 설정하고, 
  - home(index)에 보여질 함수(controller) 안에 ``res.render("home")``로 express에 설정함
  - 예) ``export const trending = (req, res) => res.render("home");``
