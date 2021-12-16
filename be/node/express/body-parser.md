# Express body-parser

## 사용법

> Express 4 버전부터는 body-parser 모듈이 내장되어 있습니다.

```javascript
// application/x-www-form-urlencoded 타입 바디 가져오기
app.use(express.urlencoded({ extended: true }));

// application/json 타입 바디 가져오기
app.use(express.json());
```

