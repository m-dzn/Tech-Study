# Mongo DB

> JS 문법을 사용하는 NoSQL DB

## 특징

1. JOIN이 없습니다.
2. JS 문법으로 질의를 합니다.
3. 쿼리가 꼬여 오류를 발생시킬 수 있습니다.
4. 확장성, 가용성이 뛰어납니다.
5. SQL과 동시에 사용할 수 있습니다.

## 용어

| RDBMS  | NoSQL      |
| ------ | ---------- |
| Table  | Collection |
| Row    | Document   |
| Column | Field      |



## 모델 생성

```javascript
const mongoose = require('mongoose');

const carSchema = mongoose.Schema(모델_스키마_객체);

const Car = mongoose.model('Car', carSchema);

module.exports = { Car }
```



## 환경 변수 분리

#### dev.js

> 개발 환경 변수를 담고 있는 모듈

#### prod.js

> 릴리즈 제품 환경 변수를 담고 있는 모듈

#### key.js

```javascript
if (process.env.NODE_ENV === 'production') {
  module.exports = require('./prod');
} else if (process.env.NODE_ENV === 'development') {
  module.exports = require('./dev');
}
```



## 구조

### 컬렉션

컬럼을 정의하지 않으며 다큐먼트별로 상이한 필드와 데이터를 넣을수 있습니다.