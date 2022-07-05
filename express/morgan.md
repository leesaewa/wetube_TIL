
## morgan
- HTTP request logger middleware for node.js
- morgan 패키지는 node.js 서버로 구성된 웹 환경에서 HTTP request 로그를 관리하기 위한 미들웨어이다.
- 좀 더 정교함. GET, path, status code 정보를 가지고 있음.

#### combined
Standard Apache combined log output.
시간, method, http버전, 사용중인 브라우저, os알려줌
``:remote-addr - :remote-user [:date[clf]] ":method :url HTTP/:http-version" :status :res[content-length] ":referrer" ":user-agent"``

#### common
Standard Apache common log output.
``:remote-addr - :remote-user [:date[clf]] ":method :url HTTP/:http-version" :status :res[content-length]``

#### dev
Concise output colored by response status for development use. The :status token will be colored green for success codes, red for server error codes, yellow for client error codes, cyan for redirection codes, and uncolored for information codes.
``:method :url :status :response-time ms - :res[content-length]``

#### short
Shorter than default, also including response time.
``:remote-addr :remote-user :method :url HTTP/:http-version :status :res[content-length] - :response-time ms``

#### tiny
The minimal output.
``:method :url :status :res[content-length] - :response-time ms``
