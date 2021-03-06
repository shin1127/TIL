# Pythonでは変数名にlistとつけてはいけない


## 予約語とは？

> 予約語とは、プログラミング言語などの人工言語の仕様に定められている、  
> 開発者が付ける識別名として利用できない文字列のこと。  
> 予約語に挙げられた単語やフレーズは変数名や関数名などに使用することはできない。  
> 
> IT用語辞典 e-Wordsより

## Pythonにおける"list"のポジションとは？

listは予約語ではないので、変数名に用いることはできる。  
とはいえ、Pythonにおけるリストの型は"list"という名前で定義されてもいる。

予約語のような気配もあるが、変数名にも使えてしまうということで、ここでは便宜上listを"準予約語"と呼ぶことにする。

## どういう問題があるの？

"list"を変数として用いているソースコードにおいて、
リストの型を調べる関数を使うと不具合が起きる。

もっと噛み砕いて説明すると、
listというワードを別の箇所ですでに使っている状態で、  
こいつの型はlistだろうか？という確認をする関数は使えないということ。

## 具体例（ソースコード）


まず、このソースを書いてしまった経緯について。  
多次元配列に関するソースコードを書きたかったのだが、  
「あれ？型を確認する関数ってどんなのだっけ？多次元配列はおいといて、とりあえず簡単なリストを作って確認してみよう」
という流れとなる。

```Python
list = [1, 2, [3, [4], 5], 6]

for i in list:
    print(i)


array = [1, 2]

print(list == type(array))

# 出力結果
# 1
# 2
# [3, [4], 5]
# 6
# False
```

変数arrayはlist型であるにも関わらず、Falseが返されていることがわかる。  

因みに、変数listを消去した以下のソースコードではTrueが返されるため、  
変数listが悪さをしていると想像できる。  
**エラーメッセージが返ってこないため、非常に混乱する上、原因が特定しづらい。**  

準予約語を使うときは十分注意しよう。というより使ってはいけない。

```Python
array = [1, 2]

print(list == type(array))

# 出力結果
# True
```
