# Non Blocking I/O

## 태스크 처리 방식

**Blocking 방식** : 이전 태스크가 모두 종료되고 나서 다음 태스크를 수행

**Non Blocking 방식** : 이전 테스크가 종료되기 전 다음 태스크를 수행

<br>

## 언제 사용할까?

1. I/O 태스크가 있어 비동기적인 처리가 필요할 때 사용합니다

2. 오래걸리는 태스크에 앞서 짧고 간단한 태스크들을 먼저 처리해야할 때 사용합니다

<br>

## 주의할 점

* 동시 처리가 불가능한 태스크는 Non Blocking 방식을 써도 동시에 처리되지 않습니다

<br>

## Non Blocking 기법

### setTimeout

```javascript
setTimeout(콜백 함수, 0);  // 태스크를 백그라운드로 보내 병렬적으로 처리
```

### setImmediate

```javascript
setImmediate(콜백 함수);
```
