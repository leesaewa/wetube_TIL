# logout
```
// logout
export const logout = (req, res) => {
  req.session.destroy();
  console.log("log out");
  return res.redirect("/");
};
```

## req.session.destroy()
- `express-session`
- `로그아웃`을 누르면 `세션을 삭제함. (사용자 정보 삭제)

## express-flash를 사용할 때
- session을 destroy하면 안 됨.
```
req.session.user = null;
res.locals.loggedInUser = req.session.user;
req.session.loggedIn = false;
```
