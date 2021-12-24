# Express | res 객체

## 메서드

### .send( )와 .json( )

>  .send( )와 .json( )은 내부적으로 서로를 호출합니다.
> 그럼에도 call stack이 오버플로우되지 않는데, 이는 .send( ) 메서드 내부의 분기문 때문입니다.

.send(object)는 .json( )을 호출하지만 .send(string)은 .json( )을 호출하지 않습니다.

.json( )은 내부에서 .send(string)을 호출하므로 스택 오버플로우 없이 상호 호출이 가능합니다.

```javascript
// 1. res.send(object) 시 함수 호출
res.send(object)
res.json(object)
res.send(string)

// 2. res.json(object) 시 함수 호출
res.json(object)
res.send(string)

// 3. res.send(string) 시 함수 호출
res.send(string)
```

# 

## 참고 자료

https://haeguri.github.io/2018/12/30/compare-response-json-send-func/