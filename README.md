# wetube_TIL

코드는 따로 올렸음.
<a href="https://github.com/leesaewa/wetube-reloaded">코드는 이쪽으로</a>

-------


## express
- <a href="https://github.com/leesaewa/wetube_TIL/blob/main/express/express_setting.md">express 설정</a>
- <a href="https://github.com/leesaewa/wetube_TIL/blob/main/express/export.md">export</a>
- <a href="https://github.com/leesaewa/wetube_TIL/blob/main/express/router.md">Router</a>
- <a href="https://github.com/leesaewa/wetube_TIL/blob/main/express/parameter.md">URL parameter</a>
- <a href="https://github.com/leesaewa/wetube_TIL/blob/main/express/parameter.md#%EC%A0%95%EA%B7%9C%EC%8B%9D">정규식</a>
- <a href="https://github.com/leesaewa/wetube_TIL/blob/main/express/middlewares.md">middlewares</a>
  - <a href="https://github.com/leesaewa/wetube_TIL/blob/main/express/morgan.md">morgan</a>
- <a href="https://github.com/leesaewa/wetube_TIL/blob/main/express/return_render.md">return, render</a>
- <a href="https://github.com/leesaewa/wetube_TIL/blob/main/express/img-upload.md">이미지 업로드하는 법</a>
- <a href="https://github.com/leesaewa/wetube_TIL/blob/main/express/form.md">form</a>



## mongoDB
- <a href="https://github.com/leesaewa/wetube_TIL/blob/main/mongoDB/guide.md">mongoDB 명령어 모음</a>
- <a href="https://github.com/leesaewa/wetube_TIL/blob/main/mongoDB/mongodb_install.md">mongo DB Install</a>
- <a href="https://github.com/leesaewa/wetube_TIL/blob/main/mongoDB/operations.md#schemas">Schemas</a>
- <a href="https://github.com/leesaewa/wetube_TIL/blob/main/study/220711.md#schema-property%EC%86%8D%EC%84%B1">schema property</a>
  - <a href="https://github.com/leesaewa/wetube_TIL/blob/main/mongoDB/schema.md">mongoose schema</a>
- <a href="https://github.com/leesaewa/wetube_TIL/blob/main/mongoDB/operations.md#models">Models</a>
- <a href="https://github.com/leesaewa/wetube_TIL/blob/main/mongoDB/operations.md#promise">Promise</a>
- <a href="https://github.com/leesaewa/wetube_TIL/blob/main/study/220711.md#exists">exists()</a>
- <a href="https://github.com/leesaewa/wetube_TIL/blob/main/study/220711.md#id%EA%B0%92-%EC%A1%B0%EC%A0%95">ID값 조정</a>



## pug
- <a href="https://github.com/leesaewa/wetube_TIL/blob/main/pug/define.md">Basic</a>
- <a href="https://github.com/leesaewa/wetube_TIL/blob/main/pug/iteration.md">iteration 반복</a>
- <a href="https://github.com/leesaewa/wetube_TIL/blob/main/pug/mixin.md">mixin</a>
- <a href="https://github.com/leesaewa/wetube_TIL/blob/main/pug/property.md">partial, extends, inheritance, if문 등~</a>
- <a href="https://github.com/leesaewa/wetube_TIL/blob/main/pug/fake_arraydb.md#%EB%A7%81%ED%81%AC%EC%97%90-%EB%B3%80%EC%88%98%EB%A5%BC-%EB%8B%B4%EB%8A%94-%EB%B2%95">변수 불러와서 쓰는 법</a>
- <a href=""></a>
- <a href=""></a>

## bug
- <a href="https://github.com/leesaewa/wetube_TIL/blob/main/bug/heroku.md">heroku SCSS 모듈을 찾을 수 없음.</a>
- <a href="https://github.com/leesaewa/wetube_TIL/blob/main/bug/github_login.md">깃허브 프로필 이미지 노출</a>



-----------

## mongo DB 설치/세팅
### chocolatey
#### 설치
``Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))``

#### chocolatey 설치 확인
``$ choco
Chocolatey v0.10.15
Please run 'choco -?' or 'choco <command> -?' for help menu.``

#### <a href="https://community.chocolatey.org/packages?q=mongodb">mongoDB 패키지 설치</a>

#### <a href="https://webigotr.tistory.com/241">mongo DB 설정</a>

#### mongoDB 설치 확인
``$ mongod``
``$ mongo`` -> mongoDB shell 확인

### mongoose
#### <a href="https://www.npmjs.com/package/mongoose">설치</a>
``$ npm install mongoose``

-----

