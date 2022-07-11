# return
```
export const home = async (req, res) => {
  const videos = await Video.find({});
  return res.render("home", { pageTitle: "Home", videos });
};
```
- 본질적인 `return`의 역할보다는 `function`을 마무리짓는 역할로 사용되고 있음.
- 이러한 경우 `return`이 없어도 정상적으로 동작하지만 실수를 방지하기 위해 return을 사용

# render한 것은 다시 render할 수 없음
- `redirect()`, `sendStatus()`, `end()` 등등 포함 (express에서 오류 발생)

