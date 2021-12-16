# Mongo DB

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



