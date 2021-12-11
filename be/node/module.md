# 모듈

> **Module이란?**
>
> 기능 단위로 분리된 JS 코드이자 앱을 구성하는 개별 요소를 말합니다.

## 특징

* 파일 단위로 분리되어 있습니다.
* 변수, 함수, 객체 등을 모듈로 내보낼 수 있습니다.

## 단점

1. 모듈이 많아질 수록 구조를 파악하기 힘듭니다.

## 사용법

### CommonJS

#### 내보내기

```javascript
const add = (a, b) => a + b;
module.exports = {
  add
};
```

#### 가져오기

```javascript
const { add } = require('모듈경로');
```

### ESM

#### 내보내기

```javascript
const add = (a, b) => a + b;

export add;
```

#### 가져오기

```javascript
import { add } from '모듈경로';
```



