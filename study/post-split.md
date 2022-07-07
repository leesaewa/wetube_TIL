# method="POST"
- form 값을 가져와서 업로드하기
- 데이터베이스에 영화를 추가하기 위해 `addMovie` 함수가 export 되어 있음.
  이 함수는 하나의 인자를 가지는데, `이 인자(argument)는 객체(object)`여야 함.


## pug

```
form(method="POST")
    input(type="text", name="title", placeholder="Title" required)
    textarea(name="synopsis", cols="30", rows="10", placeholder="Synopsis" required) 
    input(type="text", name="genres", placeholder="Genres" required)
    input(type="submit" value="Add Movie")
```

## javascript
- ``req.body``에 form값 `{ title, synopsis, genres }`를 선언.
- `{ title, synopsis, genres }` 변수를 `uploadVideo` 변수에 객체(Object)로 넣어줌.
- `addMovie` 함수에 form값이 객체로 담긴 `uploadVideo`를 인자로 넣어줌.
- `input(type="submit" value="Add Movie")` submit버튼을 누르면 `res.redirect("/")` 홈으로 리다이렉트 함.

```
export const postAdd = (req, res) => {
  const { title, synopsis, genres } = req.body;
  const uploadVideo = {
    title,
    synopsis,
    genres: genres.split(","),
  };
  addMovie(uploadVideo);
  return res.redirect("/");
};
  ```
  
# String.prototype.split()
- 문자열을 분리시키는 자바스크립트의 메서드.
- `string.split(separator, limit)`
- `separator` : 문자열을 잘라줄 구분자(문자열 or 정규식). 값이 입력되지 않으면 문자열 전체를 배열에 담아서 리턴.
- `limit` : 최대 분할 개수. 필수 아님.
- 위의 `genres: genres.split(","),`를 `console.log`로 찍어보면 `genres: [ '1', '2', '3', '4', '5', '6' ]` `,`을 기준으로 끊어져서 배열로 나옴.


# Array.prototype.map()
<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/map">참고 링크</a>
- 과제로 나온 거 아님. slack에서 나왔길래 찾아봄.
- map() 메서드는 배열 내의 모든 요소 각각에 대하여 주어진 함수를 호출한 결과를 모아 새로운 배열을 반환.
- 주로 주어진 배열의 값을 재정의 할 때 사용하는 방법.
- ECMA에는 **"주어진 배열의 값들을 오름차순으로 접근해 callbackfn을 통해 새로운 값을 정의하고 신규 배열을 만들어 반환한다"** 라고 정의됨.
- 사용하지 않은 이유: map의 정의를 아직 정확히 이해하지 못함. 그리고 배열로 반환하면 되므로 `split()`로도 충분하지 않나 생각함.

### JavaScript Demo: Array.map()
```
const array1 = [1, 4, 9, 16];

// pass a function to map
const map1 = array1.map(x => x * 2);

console.log(map1);
// expected output: Array [2, 8, 18, 32]
```

### 구문
`arr.map(callback(currentValue[, index[, array]])[, thisArg])`

#### callback
새로운 배열 요소를 생성하는 함수. 다음 세 가지 인수를 가집니다.
#### currentValue
처리할 현재 요소.
#### index (Optional)
처리할 현재 요소의 인덱스.
#### array (Optional)
`map()`을 호출한 배열.
#### thisArg (Optional)
callback을 실행할 때 `this`로 사용되는 값.



