# 백엔드 빌드

https://babeljs.io/docs/en/babel-cli
npm install --save-dev @babel/core @babel/cli

스크립트에 추가
`"start": "node build/init.js",
"build:server": "babel src -d build"`

`> npm start`는 `npm run start`로 안 해도 됨. 기본 명령어라서.

# frontend 빌드
- webpack을 `production`으로 변경해야 함.
`"build:assets": "webpack --mode=production",
"dev:assets": "webpack --mode=development"`
- `watch`모드는 `development`모드에서만 사용해야 함.
  - 삭제하고 `package.json`에 기재
  - `"dev:assets": "webpack --mode=development -w"`

Webpack Mode 설정 (두 가지 방법)
```
// 1. webpack.config.js 파일에 mode옵션을 설정하거나
module.exports = { mode: 'development' };

// 2. 또는 package.json script에 CLI 인수로 mode설정
webpack --mode=development
```
주의! 만약 Mode를 설정하지 않으면 webpack은 production(배포)를 모드의 기본값으로 설정합니다.
https://webpack.js.org/configuration/mode

Babel로 컴파일시 파일이나 폴더 무시
build:server를 할 때 포함되는 client 폴더는 필요하지 않기 때문에 아래와 같이 ignore해주시면 됩니다.
```
npx babel src --out-dir lib --ignore "src/client"
```
https://babeljs.io/docs/en/babel-cli#ignore-files

+ mode를 production으로 했음에도 코드가 한 줄로 축약되지 않으시는 분들은 optimization 옵션을 제거해주시면 됩니다.


# heroku 배포
- https://dashboard.heroku.com/ 계정 생성
- app 생성
- https://devcenter.heroku.com/articles/heroku-command-line heroku cli설치
- `$ heroku login`을 git bash나 vscode 커맨드에 입력
- 로그인하라고 뜸. -> 로그인 완료하면 연결해줌.
- 헤로쿠에 커밋할 때 branch가 main이었으면 main으로 올려야 함.
- `package.json`에 `engines`설정.
  - ` "engine": {"node": "12.16.3","npm": "6.14.8"},`

### 사용할 수 있음
$ git add .
$ git commit -am "make it better"
$ git push heroku master
$ heroku git:remote -a (생성한 앱 이름)

$ heroku logs --tail 서버에 올리는 로그를 보여줌

