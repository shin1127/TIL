# PostgresQL のクォートの扱いについて

> 「”」と「’」の違い
> PostgreSQL などの標準 SQL では、  
> シングルクォーテーションで囲う：文字列定数として扱う  
> ダブルクォーテーションで囲う：カラム名として扱う  
> という仕様になっている。  
> [えっ、まだ PostgreSQL でダブルクォーテーション使ってるの？](https://qiita.com/Sirloin/items/b14ab34415a1ebd8a9c5)

カラム名はダブルクォート、  
フィールド名（セル名）はシングルクォート

> shop=# select shohin_mei, shohin_bunrui, torokubi from shohin where torokubi < '2009-09-27'
> shop-# ;
> shohin_mei | shohin_bunrui | torokubi  
> --------------+---------------+------------
> T シャツ | 衣服 | 2009-09-20
> 穴あけパンチ | 事務用品 | 2009-09-11
> 包丁 | キッチン用品 | 2009-01-15
> 圧力鍋 | キッチン用品 | 2009-01-20
> おろしがね | キッチン用品 | 2008-04-28
> フォーク | キッチン用品 | 2009-09-20
> (6 rows)
>
> shop=# select shohin_mei, shohin_bunrui, torokubi from shohin where torokubi < '2009-09-27';
> shohin_mei | shohin_bunrui | torokubi  
> --------------+---------------+------------
> T シャツ | 衣服 | 2009-09-20
> 穴あけパンチ | 事務用品 | 2009-09-11
> 包丁 | キッチン用品 | 2009-01-15
> 圧力鍋 | キッチン用品 | 2009-01-20
> おろしがね | キッチン用品 | 2008-04-28
> フォーク | キッチン用品 | 2009-09-20
> (6 rows)

> shop=# select shohin_mei, shohin_bunrui, torokubi from shohin where torokubi < "2009-09-27";
> ERROR: column "2009-09-27" does not exist
> LINE 1: ...hin_bunrui, torokubi from shohin where torokubi < "2009-09-2...
> ^
> shop=# select shohin_mei, shohin_bunrui, torokubi from shohin where torokubi < 2009-09-27;
> ERROR: operator does not exist: date < integer
> LINE 1: ...hohin_bunrui, torokubi from shohin where torokubi < 2009-09-...
> ^
> HINT: No operator matches the given name and argument types. You might need to add explicit type casts.
