# Power Shell mongoDB 명령어

## 몽고 사용
> mongo

## 내가 가진 db 보기
> show dbs

## 현재 사용 중인 db 확인
> db

## 사용할 db 선택하기
> use dbName
(현재 수업에서는 `use wetube`)

## db 컬렉션 보기
> show collections

## db 컬렉션 안에 documents 보기
> db.collectionName.find()
(현재 수업에서는 `db.videos.find()`)

## db 컬렉션 안에 documents 내용 모두 제거하기
> db.collectionName.remove({})
(현재 수업에서는 `db.videos.remove({})`)
