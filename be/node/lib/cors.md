# CORS

## 설치

```shell
yarn add cors
```



## 사용법

### be/app.js

```javascript
const cors = require('cors');

app.use(cors());
app.use('/api', require('./routes/api'));
```
