# 형 변환

## 원시형의 형 변환

### 암시적 형 변환

JS에서 함수, 연산자로 전달된 값은 대부분 자동으로 형 변환됩니다.

### 명시적 형 변환

#### 문자열로 변환

> String(값)

```javascript
String(불린); // 'true', 'false'
String(숫자); // '1', '2', ...
String(undefined); // 'undefined'
String(null); // 'null'
String(객체); // '[object 객체_종류]'
String(Symbol(객체)) // 'Symbol([object 객체_종류])'
```

#### 숫자로 변환

> Number(값) 또는 +"숫자", -"숫자"

```javascript
Number(문자열); // '123' -> 123; '123공백외의문자' -> NaN
Number(undefined); // NaN
Number(null); // 0
Number(true); // 1
Number(false); // 0

typeof +"숫자" // "number"
```

#### 불린으로 변환

> Boolean(값)

```javascript
Boolean(숫자) // 0은 false, 그 외 true
Boolean(문자열) // 빈 문자열은 false, 그 외 true
```

