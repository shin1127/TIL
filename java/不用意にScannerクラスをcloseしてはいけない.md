# 不用意に Scanner クラスを close してはいけない

[Scanner を使った時に入力をしてないのに NoSuchElementException が発生する](https://teratail.com/questions/126925)

> count メソッドは何度も呼び出されるメソッドだと思います。その中で毎回 Scanner インスタンスを new してメソッドが終わるときに close していますね？close すると System.in も close されます。よって 2 回目にこのメソッドを呼び出したときには既に System.in は close 済みなので二度と入力処理はできません。

```java
    public int inputMoney() {
        Scanner sc = new Scanner(System.in);
        System.out.print("input money > ");
        int input = sc.nextInt();
        // sc.close();
        return input;
    }
    public int buyCommodity(int currentMoney, ArrayList<Drink> ary) {

        Scanner sc1 = new Scanner(System.in);
        System.out.print("select number > ");
        int id = sc1.nextInt();
        // int id = 1;
        currentMoney = currentMoney - ary.get(id).getValue();
        System.out.println("you bought a " + ary.get(id).getName() + ".");
        return currentMoney;
    }
```

Main クラスで inputMoney メソッド、buyCommodity メソッドを呼び出すとエラーが起きる

```
Exception in thread "main" java.util.NoSuchElementException
        at java.base/java.util.Scanner.throwFor(Scanner.java:937)
        at java.base/java.util.Scanner.next(Scanner.java:1594)
        at java.base/java.util.Scanner.nextInt(Scanner.java:2258)
        at java.base/java.util.Scanner.nextInt(Scanner.java:2212)
        at Logic.buyCommodity(Logic.java:44)
        at Main.main(Main.java:38)
```

標準入力に関して、テキストでは必ず close しようと言われるため、安易に close しがち → 問題
