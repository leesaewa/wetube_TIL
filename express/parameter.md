## URL parameters
``videoRouter.get("/:id", see);``
- ex)) ~~/lectures/숫자(변수)
- ``:id``의 ``id``는 변경돼도 상관없으나 꼭 ``:``를 정의해야 함.
- 자동으로 라우터 생성. url에 변수를 넣을 수 있게 해줌.
- ``:id``는 제일 아래에 써주는 게 좋음.
  - 만약 ``/upload``라는 라우터가 중간에 있다면 ``~~/lectures/upload``페이지가 아닌 ``:id`` 변수로 인식해버림.
  - 정규식으로 숫자만 나오게 하면 상관없음.
  
## 정규식
- 문자열로부터 특정 정보를 추출해내는 방법.
- ``(\\d+)`` -> 숫자만 나오게 함.
