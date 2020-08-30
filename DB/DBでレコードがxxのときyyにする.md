# DBでレコードがxxのときyyにする

## 環境

※ MySQLのおはなし  

## クエリ

例えばbookテーブルのpathカラムのNULL (= null)を "noimage.png"に置換する

`$ update book set path = "noimage.png" where path is null;`
