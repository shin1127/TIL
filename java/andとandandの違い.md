# $と$$の違い、あるいは|と||の違い

&において、左辺を評価するだけで結果が決まるとき右辺は評価されない  

&&において、左辺を評価するだけで結果は決定できるとしても、右辺も評価する  
→左オペランド次第で右オペランドを評価しない  
ちなみに&&とか||はショートサーキット演算子っていう  

```java
int a = 5;
boolean b = a < 3 & ++a < 10
```
&は結果が決まったとしても右オペランドを評価するので、  
`a< 3`がfalseで変数bがfalseとなることが確定したとしても、`++a < 10`を評価する→aは6になる  

ややこしいんで&&や||を使うことを推奨される気配があるってかこんなことすんな
