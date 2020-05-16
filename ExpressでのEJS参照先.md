```JS
// app.js

var express = require("express");
var app = express();

app.set("view engine", "ejs");

app.get("/", (req, res) => {
  res.status(200).render("index.ejs", { title: "webアプリケーション開発" });
});
app.listen(3000);
```

特に断りのない限り、ファイルの参照先は views/index.ejsとなるため、  
app.jsと同じフォルダにindex.ejsを格納していると、エラーが発生する。
