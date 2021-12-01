# URIComponent



## encodeURIComponent

URI 주소에는 한글을 사용하지 못하기 때문에

axios 등을 이용할 때 한글 주소는 `Percent-Encoding` 해서 요청을 보내야합니다.

**encodeURIComponent**는 이 `Percent-Encoding`을 수행하는 함수입니다.

```javascript
const result = await axios.get(
    `http://localhost:8080/api/${encodeURIComponent('상품')}`
);
```



<br>



## decodeURIComponent

`Percent-Encoding` 된 문자를 원래대로 되돌리는 함수입니다.
