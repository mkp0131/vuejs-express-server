## [vue] vue, react, spa 앱 express 서버 구축, 배포

### 설치

- spa로 서비스를 구축시 서버의 라우팅을 spa 받지 못한다.
- `connect-history-api-fallback` 설치해서 해결하자
- 공식 문서: https://www.npmjs.com/package/connect-history-api-fallback

```
npm i connect-history-api-fallback
```

### express 설정

- `static` 과 `use` 설정이 기존의 라우터보다 밑에 있어야, 기존의 라우터와 동시에 사용 가능하다.

```js
// 기존 라우터
app.use("/users", usersRouter);

// VUE JS 설정
// 기존의 라우터 보다 밑에 위치한다.
app.use(require("connect-history-api-fallback")());
app.use(express.static(path.join(__dirname, "dist")));
```

### 참고

#### [vue] 배포 환경 설정

- 공식문서: https://router.vuejs.org/guide/essentials/history-mode.html#native-node-js
