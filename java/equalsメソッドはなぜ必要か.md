# equalsメソッドはなぜ必要か

## equalsメソッドの存在を忘れて沼にハマったソースコード

```java
     public boolean stopContinue() {
         Scanner sc = new Scanner(System.in);
         System.out.println("Do you stop buying? Y or N");
         String yn = sc.nextLine();
         if (yn == "Y" || yn == "y") {
             System.out.println(yn + "show true");
             return true;
         } else if (yn == "N" || yn == "n") {
             System.out.println(yn + "show false");
             return false;
         } else {
             System.out.println(yn + "show false and");
             return false;
         }
         // return false;
 
     }
     // ここからMain.java
                 if (logic.stopContinue()) {
     
                     break;
                 }
             }
             System.out.print("Thank you!! Bye!!");
```

Y、Nを入力してもif文やelse if文でキャッチされない  
->equalsメソッドを使って比較する必要がある  

## equalsを使わないとき

equalsを使わないとき、同一インスタンスかどうかを確認している

## equalsメソッドなしでも正しく比較できるときもある　なんで？

constant poolというものがどうやら関係しているらしい（Java固有の仕様）

```java
String a1 = "aaa";
String a2 = "aaa";
System.out.println(a1 == a2); // true
contant pool領域に"aaa"が生成され、stack領域に"aaa"を指す参照値a1が生成される。
contant pool領域に"aaa"があるので、stack領域に"aaa"を指す参照値a2が生成される。
a1,a2とも"aaa"のアドレスが入っているので、trueになる。
```

[Stringとheap領域とconstant pool](https://qiita.com/liguofeng29/items/16d6dbec471bc5269f0e)
