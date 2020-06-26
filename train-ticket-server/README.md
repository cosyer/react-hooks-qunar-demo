# train-ticket-server
pm2管理api

## 用法
```sh
npm install

# 启动
npm start

# 停止
npm run stop
```

## 知识点
- index.js

```js
const express = require("express");
const path = require("path");
const apiMocker = require("mocker-api");

const app = express();

apiMocker(app, path.resolve("./mocker/mocker.js"));
app.listen(80);
```

- mocker.js
```js
module.exports = {
  "POST /rest/search"(req, res) {
    return res.json({
      code: 0,
    });
  },
  "GET /rest/cities": require("./rest/cities.json")
}
```
