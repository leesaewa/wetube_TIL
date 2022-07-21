# scss loader

## <a href="https://www.npmjs.com/package/sass-loader">scss-loader</a>
- scss파일을 css 파일로 전환시켜줌.
- `> npm install sass-loader sass webpack --save-dev`

## <a href="https://webpack.js.org/loaders/css-loader/">css-loader</a>
- `@import`와 `url()`을 풀어서 해석해줌.
- `> npm install --save-dev css-loader`

## <a href="https://webpack.js.org/loaders/style-loader/">style-loader</a>
- css를 ``DOM`에 주입.
- `> npm install --save-dev style-loader`

### <a href="https://webpack.js.org/plugins/mini-css-extract-plugin/">MiniCssExtractPlugin</a>
- `style-loader`대신 사용.
  - (style-loader를 사용하면, javascript코드가 css파일을 읽는데, 우리는 css파일 따로, js파일 따로 웹팩으로 번들화 시키고싶다. 한번에 할 경우 js 로딩을 기다려야하기 때문이다.
그래서 MiniCssExcractPlugin.loader를 사용한다.)
- 이 플러그인은 CSS를 별도의 파일로 추출함.
- CSS가 포함된 JS 파일별로 CSS 파일을 생성. `mini-css-extract-plugin`을 `css-loader와 결합`하는 것이 좋음.
- `> npm install --save-dev mini-css-extract-plugin`

## webpack에 입력
- 제일 마지막 loader부터 기재. **웹팩은 뒤에서부터 시작하기 때문**
```
{
  test: /\.scss$/,
  use: ["style-loader", "css-loader", "sass-loader"],
},
```

# Watch and WatchOptions
`watch: true,`
- Webpack은 파일이 변경될 때마다 이를 감지하여 다시 컴파일 할 수 있음.

## watch
- watch 모드를 켬.
- 초기 빌드 후 webpack은 해석 된 파일의 변경 사항을 계속 감시함. (webpack.config.js에 entry에 지정한 파일을 감시.)





