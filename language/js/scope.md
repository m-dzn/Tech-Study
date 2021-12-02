# 스코프

## 전역 스코프 (Global Scope)

<br>

## 함수 스코프 (Function Scope)

<br>

## 블록 스코프 (Block Scope)

> `{ }`, `if`, `for`, `while`, `function`, `try/catch` 문에서 { } 중괄호가 감싸고 있는 영역 범위

블록 스코프는 함수 스코프의 부분집합으로 볼 수 있습니다.

중괄호 ( { } ) 안에서 let, const 변수를 선언하면 블록 밖에서는 이 변수를 읽을 수 없습니다.

그러나 var의 경우 블록 스코프를 무시하고 안에서 선언된 변수를 사용할 수 있습니다.

```javascript
if (true) {
    let dogName = 'Volt';
    console.log(dogName);     // Volt    
}

console.log(dogName);         // Not Defined Error

if (true) {
    var catName = 'Django';
    console.log(catName);     // Django
}

console.log(catName);         // Django
```

<br>

## 어휘적 스코프 (LS; Lexical Scope)

> 함수를 선언한 위치에 따라 this가 결정되는 것을 말합니다.
> 
> *호출 위치에 따라 this가 결정되는 Dynamic Scope와 정반대의 개념입니다.*

- JS 함수들은 기본적으로 Lexical Scope를 따릅니다.

```javascript
var name = '홍길동';

function wrapper() {
    var name = '이순신';
    getName();
}
function getName() {
    console.log(name);
}

wrapper(); // '홍길동'; (getName호출 위치와 무관)
getName(); // '홍길동';
```
