
### js 나눠서 express server.js에 익스포트, 임포트하기
1. export default
- ``export default globalRouter;``
- 파일 당 한가지의 default export만 가질 수 있음. 두 개는 안 됨.
- server.js에 ``import globalRouter from "./routers/globalRouter";`` 임포트
- 임포트할 때, default 변수명을 그대로 가져오지 않고 변경을 해도 됨. 왜냐하면 default는 하나밖에 못 쓰기 때문.
  하지만 같은 이름을 유지하는 게 좋음.

2. export
- export : 여러 개를 익스포트할 수 있음.
  ``export const trending = (req, res) => res.send("home page videos");``
- 여러개를 임포트할 경우, ``import { trending } from "../controllers/videoController";``로 함.
- 임포트할 때 선언한 변수명을 그대로 가지고 와야 함. 변경하면 안됨. default와의 차이점.
