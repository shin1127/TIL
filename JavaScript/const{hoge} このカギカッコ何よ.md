# ただ変数名を入れて初期化せず、わざわざカギカッコを入れて初期化しているJSのソースコードは何なのか


## とりあえず参照したサイト

https://sbfl.net/blog/2019/08/26/javascript-bracketed-variables/  
このへんに解説が書いてある

## 試してみたこと

Udemyの講座よりサンプルコード  

```JS

const { URL } = require("url");
var url = new URL("http://game.granbluefantasy.jp/");
console.log(url.protocol);
console.log(url.host);
console.log(URL);
console.log(url);

// http:
// game.granbluefantasy.jp
// class URL { … }
// URL {Symbol(context): URLContext, Symbol(query): URLSearchParams}

```

上の参照サイトを見るに、  
変数名（変数の命名）にも何か意味があるらしい。  

このサンプルコードに置き換えて解釈すると、  

urlで読み込んだオブジェクトのURLというものをURLという変数として初期化している  

ということらしい。
URLという名前で一致させていることが重要。  
試しに"URL"を"UhogeRL"という変数に全部置き換えたら、ターミナルで怒られた。  

// URL {Symbol(context): URLContext, Symbol(query): URLSearchParams}

という出力が何を表しているかはよくわからない。  
しかし、講座の内容から離れすぎるといつまでたっても講座が終わらないので後回しにする。
