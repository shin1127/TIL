# JSの比較演算子||

いわゆるORを表す演算子だと思っていたのだが違う用途もあるらしい。

https://qiita.com/Imamotty/items/bc659569239379dded55

> 2. イディオムっぽい使い道「条件分岐の省略」
> 論理演算子はしばしば 条件分岐の省略 の為に使われます。
> 論理演算子||の左側がtrueと評価出来る場合は左側の値、
> そうでなければ右側の値を返します。

```JS

app.get("/", (req, res) => {
  var count = req.session.count || 0;
  req.session.count = count + 1;
  res.render("./index.ejs", { count });
});

```

こいつはreq.session.countが存在するならその値を返して、
なければ0を返せという意味のようだ
