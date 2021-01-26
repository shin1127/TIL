# 不用意に Scanner クラスを close してはいけない

[Scanner を使った時に入力をしてないのに NoSuchElementException が発生する](https://teratail.com/questions/126925)

> count メソッドは何度も呼び出されるメソッドだと思います。その中で毎回 Scanner インスタンスを new してメソッドが終わるときに close していますね？close すると System.in も close されます。よって 2 回目にこのメソッドを呼び出したときには既に System.in は close 済みなので二度と入力処理はできません。
