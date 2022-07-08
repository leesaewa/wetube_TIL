# mongoose `schema`
- 스키마를 정의할 때는 `타입을 가정 먼저, 그다음은 속성들을 정의`함.

## schema Type
`이름: 타입`

```
var exampleSchema = new mongoose.Schema({
   name:{
    type:String,
    required:true
   }
   age:Number
   number:Schema.Types.ObjectId
   created:{
    type:Date,
    default:Date.now
   }
   binary:Buffer,
   living:Boolean
   mixed:Schema.Types.Mixed
   array:[],
   arrayNumber:[Number],
   arrayString:[String]
});
```

##### String
문자열

##### Number
정수

##### Schema.Types.ObjectId
명시적으로 id 타입을 사용할 때는 이렇게 사용해야 함.
그리고 스키마에 정의를 안 해도 자동적으로 몽고에서는 생성함. 행을 구분하는 아이디 값으로 사용함.

##### Date
날짜를 나타냄.

##### Buffer
바이너리 타입을 사용할 때 사용함.

##### Boolean
참과 거짓만 값을 저장하고 나타냄.

##### Schema.Types.Mixed
다양한 타입을 저장할 수 있음.
객체나 배열 JSON으로 사용함. 타입이 없음

##### Array
[] = 배열.
[Number] = 정수 배열
[String] = 문자열 배열


-------

## schema Property(속성)
- 속성은 필드에 추가하여 더 많은 기능을 추가

```
var exampleSchema = mongoose.Schema({
   firstName:{
    type:String,
    required:true,
    trim:true,
    lowercase:true  
   },
});
```

##### required
필수 입력

##### unique
다른 행과 중복되면 안 됨.

##### trim
공백을 제거(문자열 타입에 사용)

##### default
문서가 생성되면 기본값으로 저장됨.

##### lowercase
대문자를 소문자로 저장함(문자열 타입)

##### match
정규식으로 저장하려는 값과 비교.

##### validate
함수로 개발자가 조건을 만듦.

##### set
값을 입력할 때 함수로 조건을 만듦.

##### get
값을 출력할 때 함수로 조건을 만듦.

##### ref
해당하는 모델을 참조할 때 사용.


### 타입과 속성을 넣었을 때 예시
```
const movieSchema = new mongoose.Schema({
  title: { type: String, required: true },
  summary: { type: String, required: true },
  year: { type: Number, required: true },
  rating: { type: Number, required: true },
  genres: [{ type: String, required: true }],
});
```
- 배열은 `[String]` 또는 `[{ type: String }]`로도 나타낼 수 있음.
