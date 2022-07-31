# 깃허브로 로그인하면 프로필 이미지가 노출이 안됨
### 문제
<img src="https://user-images.githubusercontent.com/97646713/182016685-1ec64578-6ab4-4e72-9b3b-0fc855dc2fab.png" width="100%">
- 위 캡쳐처럼 이미지 url은 정상이나, 노출이 되지 않음.

- 콘솔에 이런 에러가 뜸.

> net::ERR_BLOCKED_BY_RESPONSE.NotSameOriginAfterDefaultedToSameOriginByCoep 200 (net::ERR_BLOCKED_BY_RESPONSE.Cope 200에 의해 동일한 원점으로 기본 설정된 후 동일한 원점이 아님)

- 뭔 소리얌...ㅠㅠ

### 알아낸 것
- `require-corp`은 동영상 녹화할 때 에러가 나서 넣었던 것.
> require-corp 를 사용하여 COEP를 활성화 하고 로드해야 하는 교차 출처 리소스가 있는 경우 <a href="https://runebook.dev/ko/docs/http/cors">CORS</a> 를 지원 해야 하며 COEP에서 차단되지 않도록 리소스를 다른 출처에서 로드 가능한 것으로 명시적으로 표시해야 합니다. 예를 들어 타사 사이트에서 이 이미지에 대해 <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/crossorigin">crossorigin</a> 속성을 사용할 수 있습니다.
- Same-origin policy:동일 출처 정책
- 짧은 지식으로 이해하기로는, 지금 네 사이트는 동일 출처 정책을 사용하고 있는데, 보안상 github라는 다른 출처에서 가져온 리소스의 상호작용을 제한했음. 그러니, 교차 출처로 접근 허용하셈. 같음.
  - **그래도 이해가 안 되는 부분이 너무 많아서 공부가 필요함.**

### 해결
- `server.js`에 설정해놨던 `res.header("Cross-Origin-Embedder-Policy", "require-corp");` -> `"require-corp"`를 `"credentialless"`로 바꿔주면 이미지가 제대로 뜸.
- `crossorigin="use-credentials"`를 `img`에 넣으라는데 나는 넣으면 안 나옴... *서버에 올리면 또 에러뜰지도 몰라서 기록함.*
- **use-credentials** : Request uses CORS headers, credentials flag is set to `include`.
  - 요청에 CORS 헤더를 사용하고 자격 증명 플래그가 `포함`으로 설정됨

```
app.use((req, res, next) => {
  res.header("Cross-Origin-Embedder-Policy", "credentialless");
  res.header("Cross-Origin-Opener-Policy", "same-origin");
  next();
});
```

### 다른 방법
- `server.js`에 `res.header("Cross-Origin-Embedder-Policy", "require-corp");` -> `"require-corp"`를 바꾸지 않고, `img`에 `crossorigin`만 넣어줘도 제대로 출력된 걸 확인 *->했으나, 서버에 올리면 에러 뜰 확률 많음.*
```
app.use((req, res, next) => {
  res.header("Cross-Origin-Embedder-Policy", "require-corp");
  res.header("Cross-Origin-Opener-Policy", "same-origin");
  next();
});

img(src=`${loggedInUser.socialOnly ? "":"/"}` + loggedInUser.avatarUrl, crossorigin)
```

## 참고 링크
- <a href="https://velog.io/@leesyong/TIL-211220">해결 참고 링크</a>
- <a href="https://developer.mozilla.org/ko/docs/Web/Security/Same-origin_policy">동일 출처 정책(same-origin policy)</a>
- <a href="https://runebook.dev/ko/docs/http/headers/cross-origin-embedder-policy">Cross-Origin-Embedder-Policy</a>
- <a href="https://runebook.dev/ko/docs/html/attributes/crossorigin">HTML 속성 : crossorigin</a>
- <a href=""></a>



