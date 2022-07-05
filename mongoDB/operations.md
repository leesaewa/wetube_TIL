## CRUD operations
- Create(생성)
- Read(읽기)
- Update(수정)
- Delete(삭제)

## Schemas
- mongoose의 모든 것은 스키마로 시작함.
- 각 스키마는 MongoDB 컬렉션에 매핑되고 해당 컬렉션 내 문서의 모양을 정의함.
https://mongoosejs.com/docs/guide.html#schemas

## Models
``mongoose.model(modelName, schema):``
- 모델은 스키마 정의에서 컴파일된 멋진 생성자.
- 모델의 인스턴스를 document라고 함.
- 모델은 기본 MongoDB 데이터베이스에서 문서를 만들고 읽음.
https://mongoosejs.com/docs/guide.html#models
https://mongoosejs.com/docs/models.html

## Promise
- callback의 최신버전
- promise(async-await)를 통한 외부 데이터베이스 비동기처리
- 

### 비동기(Asynchronous)란?
- 작업을 요청하지만 결과는 그 자리에서 꼭 받지 않아도 되는 데이터 처리 방식.
> 카페에서 커피를 주문할 때, 앞사람이 주문을 하고 주문한 커피를 다 제공한 다음, 다음 사람의 주문을 받는다면 **동기적 처리**라고 볼 수 있다. 반대로 모든 사람의 주문을 한꺼번에 받고 커피가 완성되는 대로 사람들에게 커피를 제공한다면 **비동기적 처리**이다.

### Async Await
```
video.find({}, (error, videos) => {
if(error){
return res.render("server-error")
}
return res.render("home")
});

===same thing

export const home = async (req, res) => {
try {
const videos = await video.find({});
return res.render("home", { pageTitle: "Home", videos });
} catch {
return res.render("server-error");
}
};
```
- async(비동기) -- await(수행될 때까지 기다려줌)
- callback function 의 장점은 에러들을 바로 볼 수 있다는 것.
- js의 단점은 기다리는 기능이 없어서 아무리 위에서 아래로 읽어도 database에서 불러오는 시간이 있어서 순서가 꼬임. 그래서 callback function을 씀.

- await는 database에게 결과값을 받을때까지 js가 기다리게 해줄 수 있음.
- await,async의 장점은 매우 직관점이라는것. 즉, js가 어디서 어떻게 기다리는지 알 수 있음.
- await는 규칙상 function이 async 상태일때만 안에서 사용 가능!
- 그러나, callback function과 달리 promise방식은 error 가 어디서 오는지 명확하지가 않음.
  - try catch를 써서 에러를 받음.
  - 말그대로 try 안에 있는 코드를 실행해보고 오류가 생기면 catch 안에 코드가 실행되는 구조.
