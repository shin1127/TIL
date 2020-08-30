mongoDBを操作するためのライブラリは2.2とか3.0とかある  
メジャーなバージョンチェンジなので注意が必要（関数が動作しないことがある）  

それを踏まえた上で3.0の場合のDB接続方法  
 
```JS

var MongoClient = require("mongodb").MongoClient;
var url = "mongodb://127.0.0.1/";
MongoClient.connect(url, (error, client) => {
  var db = client.db("sample");
  db.createCollection("test", (error, collection) => {
    client.close();
  });
});

```

事前に`npm install mongodb@3.0`とする  
@以下はバージョンだが指定しなければ最新がインストールされる  

事前にmongoDBでsampleというデータベースを作成しておかないとダメかもしれない  
