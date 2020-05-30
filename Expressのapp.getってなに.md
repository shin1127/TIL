# JSフレームワークで使う、Expressのapp.getとかapp.useとかのappってなによ

express()といちいち書くのは面倒なので、appという変数名に置き換えているだけにすぎない  

[公式リファレンス](https://expressjs.com/ja/guide/routing.html)  

```JS
var express = require('express')
var app = express()

// respond with "hello world" when a GET request is made to the homepage
app.get('/', function (req, res) {
  res.send('hello world')
})
```

expressモジュールをimport  
express()メソッド、というものはいちいち書きづらいので、appという変数名に置き換えている  

なのでappではなくexpress()を使って、

```
express().get('/', function (req, res) {
  res.send('hello world')
  ```
  
  と表記しても全く同じ挙動を示す。
