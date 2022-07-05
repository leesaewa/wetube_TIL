## mongo DB 설치/세팅

### chocolatey

#### 설치

`Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))`

#### chocolatey 설치 확인

`$ choco Chocolatey v0.10.15 Please run 'choco -?' or 'choco <command> -?' for help menu.`

#### <a href="https://community.chocolatey.org/packages?q=mongodb">mongoDB 패키지 설치</a>

#### <a href="https://webigotr.tistory.com/241">mongo DB 설정</a>

#### mongoDB 설치 확인

`$ mongod`
`$ mongo` -> mongoDB shell 확인

### mongoose

#### <a href="https://www.npmjs.com/package/mongoose">설치</a>

`$ npm install mongoose`
