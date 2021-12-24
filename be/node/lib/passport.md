# Passport 라이브러리

> 회원가입, 로그인 시 세션 & 쿠키 자동 처리

## 의존성

```shell
yarn add passport bcryptㅓ passport-local
```

## 기본 사용 코드

**app.js**

```javascript
const passport = require("passport");

const passportConfig = require("./passport");
passportConfig();

app.use(passport.initialize());
app.use(passport.session()); // 반드시 express-session보다 아래에서 설정할 것
```

## 메서드

### serializeUser

* 로그인 시 호출
* done 함수
  * 매개변수1 : 에러 발생 시 err 전달
  * 매개변수2 : req.session에 전달할 user 데이터 객체 전달

### deserializeUser

> deserializeUser는 식별자를 이용해 user 정보를 조회하는 작업을 수행니다.
> 
> 세션에 최소한의 정보만 담기 위해 수행하는 작업입니다.

* 클라이언트 요청이 올 때마다 호출
* 매개변수1 : req.session에 담겨 있는 user 정보
  * → 주로 식별자가 담겨있습니다. (이 식별자로 DB에 있는 User 정보를 가져와야하기 때문입니다.)
* 매개변수2 : done 함수 (serializeUser와 동일)
  * DB에서 찾은 user 정보는 done 함수를 통해 req.user에 저장됩니다.

## Local 로그인 구현

```javascript

```
