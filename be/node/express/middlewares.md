# Express 미들 웨어

> **Express에서 미들웨어란?**
> `function (req, res, next) { }` 형태를 갖고 클라이언트-서버 간 요청 / 응답 과정 중간에 추가되어 작업을 수행하는 함수를 말합니다.

## 종류

1. 애플리케이션 레벨 미들웨어
   
   app.use( ) 및 app.METHOD( )에 바인드되는 미들웨어

2. 라우터 레벨 미들웨어
   
   express.Router( ) 인스턴스에 바인드 되는 미들웨어

3. 오류 처리 미들웨어
   
   (err, req, res, next) 로 err 객체를 매개변수로 갖는 미들웨어

4. Built-in 미들웨어
   
   express.static (Express의 정적 자원을 다루는 미들웨어)

5. Third Party 미들웨어
   
   다른 개발자가 만들어 놓은 미들웨어

## Built-in 미들웨어

### express.static

> 정적 자원을 다루기 위한 미들웨어

```javascript
app.use(express.static('정적 자원이 위치한 디렉토리명'));
```

## Thirt Party 미들웨어

### body-parser

> Express 4 버전부터는 body-parser 모듈이 내장되어 있습니다.

```javascript
// application/x-www-form-urlencoded 타입 바디 가져오기
app.use(express.urlencoded({ extended: true }));

// application/json 타입 바디 가져오기
app.use(express.json());
```

### compression

> 리소스 압축용 라이브러리

```javascript
const compression = require('compression');

app.use(compression());
```

### express-session

```javascript
const session = require("express-session");

app.use(
    session({
        secret: process.env.SESSION_SECRET,
        resave: false, // session 값이 바뀌지 않은 경우 저장소에 저장 x
        saveUninitialized: true, // session이 필요하기 전까지는 구동 x
    })
);
```
