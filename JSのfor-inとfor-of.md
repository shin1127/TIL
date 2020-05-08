# JSの"for-in"や"for-of"は、JavaやPythonの拡張forと似ているが全然違う


## Javaの拡張for文  

for (h : hoge)  
は、配列hogeのリテラルを順にhに格納してあれやこれやと処理する。
このとき要素の番号は取得できない。

## JSのfor in文

Pytonにも同じ単語を使った拡張for文がある。

for h in hoge:
    pass
    
みたいな。
これも上のJavaの拡張for文と同じ処理を行う。（リテラルを取り出す）  
ところが、JSのfor-inは違う。  

リテラルではなく、要素の番号をhに格納して順に処理を行う。  

for (var i = 0; i < hoge.length; i++){
}

for i in hoge{
}

つまり、この上2つが同じ処理をする。

## JSのfor of文

こっちがいわゆるJavaの for (h : hoge)や、Pythonの for i in hoge に対応する。

