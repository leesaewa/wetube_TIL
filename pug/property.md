### partial
- 반복작업을 따로 만들어서 include할 수 있음!!! 이게 강점임. it was cool
- ``include partials/footer``

### inheritance(상속) / extends(확장)
```
doctype html 
html(lang="ko")
  head
    title #{pageTitle} | Wetube

  body 
    block content
  include partials/footer
  ```

- 베이스를 만들어서 그 베이스를 기준으로 확장시켜 가는 것.
- 베이스 안에 block이나 variable을 만들 수 있음.
- 
#### block
  - block = ``extends base``
  - 
#### 변수
  - 변수는 #{}로 작성해야 함.
  - 변수만 작성하고 싶을 경우에는 이렇게 함. (변수와 텍스트를 섞어쓰지 않을 경우)
    - ``h1=pageTitle``
  - ``res.render("home", {pageTitle: "Home"}``
  - render는 2개의 argument를 받음. 하나는 ``view``, 다른 하나는 ``템플릿에 보낼 변수(pug)``


## conditionals
```
if fakeUser.loggedIn
            li 
              a(href="/logout") Log Out
          else
            li 
              a(href="/login") Login
```
- JS의 if문과 똑같음.
