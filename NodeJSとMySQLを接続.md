# Node.jsでMySQL（MariaDB）を操作する
下は

- 接続に成功したかどうかを表示する
- クエリの実行結果を表示する
- fieldを表示する（fieldって何？）

```JS
var mysql = require("mysql"); // mysql操作用のライブラリ

var connection = mysql.createConnection({
  host: "localhost",
  user: "root",
  password: "1234",
  database: "db1",
});

connection.connect(function (err) {
  if (err) throw err;
  console.log("Connected");

  const sql = "select * from book";
  connection.query(sql, function (err, result, field) {
    if (err) throw err;
    console.log("table shows");
    console.log(result);
    console.log(field);
  });
});

// result（第二引数）はクエリ実行内容が格納される
// fieldはなんやろね　使わない時は第三引数指定しなくてもOK

```
Connected
table shows
[
  RowDataPacket {
    title: 'スッキリわかるJava入門',
    author: '中山清喬',
    publisher: 'インプレス\r'
  },
  RowDataPacket {
    title: 'スッキリわかるJava入門 実践編',
    author: '中山清喬',
    publisher: 'インプレス\r'
  },
  RowDataPacket {
    title: 'スッキリわかるサーブレット & JSP入門',
    author: '国本大悟',
    publisher: 'インプレス\r'
  },
  RowDataPacket {
    title: 'Pythonチュートリアル',
    author: 'Guido van Rossum',
    publisher: "o'reilly\r"
  },
  RowDataPacket {
    title: '図解でわかる統計解析',
    author: '前野昌弘 三國彰',
    publisher: ' 日本実業出版社\r'
  },
  RowDataPacket {
    title: '考える技術としての統計学',
    author: '飯田泰之',
    publisher: 'NHKブックス\r'
  },
  RowDataPacket {
    title: '手に取るように心理学がわかる本',
    author: '渋谷昌三 小野寺敦子',
    publisher: ' かんき出版\r'
  },
  RowDataPacket {
    title: '基礎からのMySQL改訂版',
    author: '西沢夢路',
    publisher: 'SB Creative'
  }
]
[
  FieldPacket {
    catalog: 'def',
    db: 'db1',
    table: 'book',
    orgTable: 'book',
    name: 'title',
    orgName: 'title',
    charsetNr: 45,
    length: 120,
    type: 253,
    flags: 0,
    decimals: 0,
    default: undefined,
    zeroFill: false,
    protocol41: true
  },
  FieldPacket {
    catalog: 'def',
    db: 'db1',
    table: 'book',
    orgTable: 'book',
    name: 'author',
    orgName: 'author',
    charsetNr: 45,
    length: 120,
    type: 253,
    flags: 0,
    decimals: 0,
    default: undefined,
    zeroFill: false,
    protocol41: true
  },
  FieldPacket {
    catalog: 'def',
    db: 'db1',
    table: 'book',
    orgTable: 'book',
    name: 'publisher',
    orgName: 'publisher',
    charsetNr: 45,
    length: 120,
    type: 253,
    flags: 0,
    decimals: 0,
    default: undefined,
    zeroFill: false,
    protocol41: true
  }
]
```
