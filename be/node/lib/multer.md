# Node | multer 파일 업로드

> 파일 업로드를 위한 Node 라이브러리입니다.

```javascript
const upload = multer({ dest: "저장할 경로" });

router.post("매핑 경로", upload.single("인풋 name"), (req, res, next) => {

});
```

## file 속성
- fieldname : input 필드명
- originalname : 원본 파일명
- encoding : 인코딩 방식
- mimetype : MIME 타입
- destination : 저장 디렉토리
- filename : 파일명
- path : 저장 경로 및 파일명
- size : 용량