# 타입

## 데이터 타입의 종류

* undefined : 값이 할당되지 않은 상태
* Boolean
* Number
  
  * 정수 & 부동소수점 수가 합쳐진 것
  * Infinity
  * -Infinity
  * NaN
* BigInt
  * IE에서는 지원 x
* String
* Symbol (ECMAScript 6에 추가)
  * 객체 고유의 식별자로 활용

## 데이터 구조 유형

* Object

  * Function : 함수를 나타내는 객체형의 일종

* null : '존재하지 않는', '빈' 값을 나타내는 값
  
  * typeof로 확인해보면 **object**라고 출력
    
    → null은 객체가 아님
    
    → 하위 호환성을 유지하기 위해 남긴 유산
  
  * 다른 언어와는 달리 Null Pointer를 의미하지 않음



## 타입 검사

> 방식 1. typeof 연산자 ( ex: typeof 변수 )
> 방식 2. typeof 함수 ( ex: typeof (변수) )

```javascript
typeof 함수 // "function"

// 함수형은 객체형의 일종입니다.
// 별도로 함수형이라는 자료형이 있는 것은 아닙니다.
```

