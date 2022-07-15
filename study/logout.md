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
