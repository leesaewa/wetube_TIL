## mixin
- scss랑 비슷한 역할인듯.
- html 코드를 재사용할 수 있게 해줌.
- partial이긴 하지만 데이터를 받을 수 있는 똑똑한 partial을 의미함.

```
-controller-
const videos = [
{
title: "First Video",
rating: 5,
comments: 2,
createdAt: "2 minutes ago",
views: 62,
id: 1,
}
]

-mixin-
mixin video(info)
div
h4=info.title
ul
li #{info.rating}/5.
li #{info.comments}/comments.
li Posted #{info.created}.
li #{info.views} views.

-pug-
include mixins/video

each info in videos
+video(info)
```
