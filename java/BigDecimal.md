# BigDecimalクラスとは

## 概要

浮動小数点型などの演算で発生する丸め誤差を回避できるクラス。  
会計など1円でも間違えられない場合に使う。  

競技プログラミングでも使いそう。  
Pythonなど他の言語でもdecimal型などの名前で同等のものが用意されている。


## 使い方

### 数値を用意する

例:整数10000をBigDecimalクラスで用意したい  
`BigDecimal tenk = BigDecimal.valueOf(10000);`

すでに宣言したString型のリテラルをBigDecimalクラスに代入したい  

```java
String p = Integer.toString(100 - sc.nextInt());`
BigDecimal pp = new BigDecimal(p);
```

### 計算する
`演算される変数名.メソッド名(演算に組み込む変数);`

```java
// mmやppは初期化されているものとする
BigDecimal result = mm.multiply(pp);
result = result.multiply(qq);
result = result.divide(tenk);
```

乗算はmultiply, 除算はdivide,  
加算はadd, 減算はsubtractを使う


# 参考
- [Java BigDecimal 足し算, 引き算, 掛け算, 割り算そして四捨五入する方法](https://www.saka-en.com/java/java-bigdecimal/)
- [クラスBigDecimal](https://docs.oracle.com/javase/jp/8/docs/api/java/math/BigDecimal.html)
