
## iteration
- 반복. each A in B = array B에있는것들을 A에 반복하여 나열.
- Pug는 each와 while라는 두 가지 기본 반복 방법을 지원함.
```
ul
each val in [1, 2, 3, 4, 5]
li= val
```
- 배열이나 객체에 반복할 값이 없으면 실행될 else 블록을 추가할 수도 있음.
  - 이 때 else는 js가 아님. 
```
- var values = [];
ul
each val in values
li= val
else
li There are no values
```

- array설정해주기
- array 넣을 템플릿에 가서
  each video(anything whatever you want) in videos(videoController에서 설정해준 array)
  li=video(same thing value before videoController에서 설정해준 array)

