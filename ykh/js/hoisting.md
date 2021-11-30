# 호이스팅

> **호이스팅이란?**
> 한 컨텍스트가 실행되면 가장 먼저 var, let, const 변수와 함수부터 우선 수집되어 자동 선언되는 JS Lexical Environment의 동작 원리를 지칭하는 용어입니다

> Creation Phase가 Execution Phase에 앞서 수행되면서 발생하는 현상입니다

* 변수 값 할당은 호이스팅과 무관하며 다른 언어에서처럼 순차적으로 일어납니다
* var 변수들이 같은 Lexical Environment 안에서는 작성된 위치와 무관하게 코드 최상단에 우선 선언된 것처럼 쓰입니다

## let과 const

var는 언제든지 재선언과 재할당이 가능합니다

let과 const는 Lexical Environment 내에서 한 번만 선언 가능합니다

**var** : hoisting 될 때 값이 undefined로 초기화됩니다. 그래서 선언 전에도 사용할 수 있습니다

**let** : hoisting 되지만 hoisting 시 변수가 초기화되지 않아 **Temporal Dead Zone**이 나타납니다. 선언한 라인에서 undefined로 초기화되므로 그 다음 라인부터 사용할 수 있습니다

**const** : let과 비슷하지만 선언과 초기화를 동시에 해야하고 재할당할 수 없습니다

## Temporal Dead Zone



## 함수

### 함수 선언문 (Function Declaration)

선언 전에도 사용 가능합니다

```javascript
test(); // hi 출력

function test() {
    console.log('hi');
}
```

### 함수 표현식 (Function Expression)

선언 전에는 사용이 불가능합니다

```javascript
test(); // Uncaught TypeError : test is not a function

var test = function() {
    console.log('hi');
}
```
