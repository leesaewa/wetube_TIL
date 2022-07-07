```
export const filterMovie = (req, res) => {
  console.log(req.query);
  const { year, rating } = req.query;
  try {
    const movies = year
      ? getMovieByMinimumYear(year)
      : getMovieByMinimumRating(rating);
    return res.render("filter", {
      pageTitle: `Searching By ${year ? "year" : "rating"} : ${
        year ? year : rating
      }`,
      movies,
    });
  } catch (error) {
    res.redirect("/");
  }
};
```

# 삼항 조건 연산자
- **조건부 삼항 연산자** 는 JavaScript에서 세 개의 피연산자를 취할 수 있는 유일한 연산자.
- 맨 앞에 조건문 들어가고, 그 뒤로 물음표`(?)`와 조건이 `참(truthy)`이라면 실행할 식이 물음표 뒤로 들어감.
- 바로 뒤로 콜론`(:)`이 들어가며 조건이 `거짓(falsy)`이라면 실행할 식이 마지막에 들어감. 보통 `if 명령문의 단축 형태`로 쓰임.

### JavaScript Demo: Expressions - Conditional operator
```
function getFee(isMember) {
  return (isMember ? '$2.00' : '$10.00');
}

console.log(getFee(true));
// expected output: "$2.00"

console.log(getFee(false));
// expected output: "$10.00"

console.log(getFee(null));
// expected output: "$10.00"
```

## 예시
`condition ? exprIfTrue : exprIfFalse `

#### condition (조건문)
조건문으로 들어갈 표현식
#### exprIfTrue (참일 때 실행할 식)
`condition`이 `Truthy`일 때 실행되는 표현식. (`true`일 때 치환될 값).
#### exprIfFalse (거짓일 때 실행할 식)
`condition`이 `falsy`일 때 실행되는 표현식. (`false`일 때 치환될 값).


# try...catch 에러 핸들링
```
try {
  nonExistentFunction();
} catch (error) {
  console.error(error);
  // expected output: ReferenceError: nonExistentFunction is not defined
  // Note - error messages will vary depending on browser
}
```
<a href="https://ko.javascript.info/try-catch">참고 링크</a>
- if문을 사용하지 않은 이유: react배울 때 말고는 try...catch는 한번도 사용해본 적이 없어서 공부 겸 사용해봄.
  또한, 에러가 날 때는 `res.redirect("/")`를 하기 때문에 사용함.
  
- `try...catch` 문은 실행할 코드블럭을 표시하고 `예외(exception)`가 `발생(throw)`할 경우의 응답을 지정함.
- 에러가 발생하면 스크립트는 ‘죽고’(즉시 중단되고), 콘솔에 에러가 출력되지만, `try..catch` 문법을 사용하면 스크립트가 죽는 걸 방지하고, 에러를 `‘잡아서(catch)’` 더 합당한 무언가를 할 수 있게 됨.

### 문법
```
try {
  try_statements
}
[catch (exception_var) {
  catch_statements
}]
[finally {
  finally_statements
}]
```

#### try_statements
실행될 선언들
#### catch_statements
`try` 블록에서 예외가 발생했을 때 실행될 선언들
#### exception_var
`catch` 블록과 관련된 예외 객체를 담기 위한 식별자
#### finally_statements
`try` 선언이 완료된 이후에 실행된 선언들. 이 선언들은 예외 발생 여부와 상관없이 실행됨.

