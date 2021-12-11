# Node 내장 객체

## global

### 특징

1. 전역 객체 : 모든 파일에서 접근 가능합니다.
2. global의 속성 및 메서드는 global prefix를 생략하고 사용 가능합니다.

### 예시

```javascript
require
console
message
```

### console

```javascript
console.log(값); // 값 출력
console.time(시간); & console.timeEnd(시간);  // 시간 간격 측정
console.dir(객체, 옵션); // 출력할 객체
console.table(배열); // 객체 속성이 표로 출력
console.trace(레이블); // 에러가 발생한 위치를 표시
```

### Timer

```javascript
setTimeout(콜백 함수, 밀리초); // 일정 시간 후 콜백 함수 호출
setImmediate(콜백 함수); // 콜백 함수를 즉시 비동기로 실행
setInterval(콜백 함수, 밀리초); // 일정 주기마다 콜백 함수 호출

clearTimeout(식별자);
clearImmediate(식별자);
clearInterval(식별자);
```

* `setImmediate(콜백 함수);`와 `setTimeout(콜백 함수, 0);` 의 실행 순서는?
  * 경우에 따라 다릅니다.

### 경로

__filename : 현재 파일명

__dirname : 현재 파일 경로