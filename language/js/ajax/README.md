# AJAX

### XMLHttpRequest

브라우저에서 기본적으로 제공하는AJAX 통신을 위한 객체입니다.

* XML이라는 이름이 들어가 있지만 XML 뿐만 아니라 JSON 등 다른 형식의 데이터를 주고 받을 수도 있습니다.

## axios

> 비동기 통신을 위한  XMLHttpRequest 를 쉽게 사용할 수 있게 해주는 라이브러리

* axios 메서드들은 Promise를 반환합니다.
  * .then과 .catch를 통해 결과 및 예외를 처리할 수 있습니다.
  * async/await 문법을 적용할 수 있습니다.

```javascript
async function() {
    const response = await axios.request({
        method: 'GET',
        url: '서버 요청 url',
        headers: {'content-Type': 'application/json'}
    });
}
```
