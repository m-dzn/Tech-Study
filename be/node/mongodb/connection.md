# Mongo DB 연결하기



app.js

```javascript
const mongoose = require('mongoose');
mongoose.connect('몽고DB 연결 URI', {
  useNewUrlParser: true,		// mongoose5 버전부터 반드시 추가해줘야 하는 옵션
  useUnifiedTopology: true	// 새 Discover & Monitoring 엔진을 사용하기 위한 옵션 (이전 버전은 deperecated 됨)
}).then(() => console.log('MongoDB Connected...'))
.catch(err => console.log(err));
```

