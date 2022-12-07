# fly.io로 배포
- 기존에 배포중이던 `heroku`가 무료가 아닌 유료로 전환됨.
- 후보 <a href="">`fly.io`</a>, <a href="https://www.koyeb.com/">`koyeb`</a> 중에서 `fly.io`로 재배포할 것을 선택함.
  - 물론 데이터베이스 다 날라가서 처음부터 다시 시작해야 함 ㅠㅠ (시간이 좀 걸릴 듯...ㅠㅠ)

## 배포 중 에러
### failed to fetch an image or build from source:~~~
<img src="https://user-images.githubusercontent.com/97646713/206199555-580da194-f514-48b7-9eb3-5a15f4aa5da1.png">
- 배포를 따라가다 보면 위와 같은 에러가 뜰 수 있음... 어떻게 해야 할지 모르겠고 난감하고... 그럴 때 도커 파일을 뜯어보고 있다가 발견함.

#### 1. `Dockerfile` 안에 아래와 같은 글이 주석으로 처리되어 있음.
<img src="https://user-images.githubusercontent.com/97646713/206200505-a8899267-570d-4565-8c17-4f5c779ade29.png">

> NPM will not install any package listed in "devDependencies" when NODE_ENV is set to "production",
> to install all modules: "npm install --production=false".
> NODE_ENV가 "운영"으로 설정된 경우 NPM은 "devDependencies"에 나열된 패키지를 설치하지 않습니다.
> 모든 모듈을 설치합니다. "npm install --production=false"

- 아마도 바벨의 경우에는 `devDependencies`라서 production으로 설정될 경우에는 인식을 못하는 것 같음.

#### 2. `RUN npm install && npm run build`로 되어 있는 부분을 고쳐줌.
<img src="https://user-images.githubusercontent.com/97646713/206200204-9fd38b39-b886-455e-b4dc-5c8ce685a476.png">
- 그 아래를 찾아 보면 `RUN npm install && npm run build`라고 되어 있는 부분이 있음.
- 그 `npm install` 뒷 부분에 `--production=false`를 추가해주면 제대로 `deploy`되는 걸 확인할 수가 있음!!!
<img src="https://user-images.githubusercontent.com/97646713/206200695-e184f867-c5ff-4ec2-a614-06b7003ae4a3.png">
> RUN npm install --production=false && npm run build
