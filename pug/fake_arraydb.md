
# Array database (가짜 데이터베이스로 샘플 비디오 만들기)

## array database와 HTML 상호작용 과정
1. 각 비디오에 id 부여
2. id를 기반으로 비디오마다 anchor 생성
3. 임의의 id를 가진 url에 접근하려고 할 때, 해당 id를 가져와서 변수에 저장
4. 저장된 id를 기반으로 해당 id 에 해당하는 object를 변수에 저장
5. 저장된 object를 기반으로 HTML 렌더링하여 contents 출력

```
const { id } = req.params;
const id = req.params.id;
```

## 링크에 변수를 담는 법
- 대상: href, class, id
1. ``a(href=`/videos/${video.id}`)=video.title``
2. ``a(href="/videos/" + video.id)=video.title``

## ternary operator
- 만약 조회수가 ``1``일 때, ``views``가 아닌 ``view``가 출력되도록 함.
  ``h3 #{video.views} #{video.views === 1 ? "view" : "views"}`` inline if문
  -> 만약 video.views가 1과 같다면 'view'를, 같지 않다면 'views'를 보여줌.
