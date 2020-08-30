# 自分の考えた、%を使わないFizzBuzzアプローチ方法

自分の考えたソースコードが完成次第、他のアプローチ方法も調べていく

## よくしられているFizzBuzzとは

面倒なのでPythonで書く
与えられた入力に対して、

```Py

if n % 15 == 0:
    return "FizzBuzz"
elif n % 3 == 0:
    return "Fizz"
elif n % 5 == 0:
    return "Buzz"
else:
    return n
    
```
という、%表記を使って余剰が0になる場合を探す方法がよくしられている。

##  n % 3 == 0 と等価な処理

各桁の数の総和が3の倍数であればよい  
例えば、100k + 10 n + 1 m..(k, n, mは任意の整数) における、 k + n + mの解が3の倍数であればよい  
与えられた数が3桁なら、ぜいぜい取りうる範囲は1から27だが（100から999）  

9999999999のように、桁の数が多いととんでもないことになるため、  
再帰処理を用いて各桁の総和を減らしていく  

最終的に1桁まで縮めることで、その数が3, 6, 9のいずれかかそうでないかという判定方法で等価な処理を行うことができるはずだ。  

## n % 5 == 0 と等価な処理

一の位の数が0か5である、0でない整数であればよい

与えられた数を文字列として扱い、-1番目の文字を調べる
与えられた数の桁数が1なら、-1番目の値が5であるときだけtrue,
それ以外なら-1番目の値が0, 5のときにtrueを返す。

## 作ったソースコード

```JS

function calc3a(n){
    n = String(n);
    array = n.split("");
    str = [];
    for (s of array){
        str.push(parseInt(s));
    }
    sum = 0;
    for (n of str){
        sum += n;
    }
    return sum;
}

function calc3b(n){
    if(n <= 9){
        return n;
    }
    return calc3b(calc3a(n));
}

function calc3c(n){
    if (calc3b(n) == 3 || calc3b(n) == 6 || calc3b(n) == 9){
        return true;
    }
    else{
        return false;
    }
}

function calc5a(n){
    n = String(n);
    nLen = n.length;
    array = n.split("");
    lastNum = array.slice(-1)
    
    if (nLen > 0){
        if (lastNum == 0 || lastNum == 5){
            return true;
        }
        else{
            return false;
        }
    }
    else{
        if (lastNum == 5){
            return true;
        }
        else{
            return false;
        }
    }
    
}

function fzbz(n){
    for (var i = 1; i <= n; i++){
        if (calc3c(i) && calc5a(i)){
            console.log("FizzBuzz");
        }
        else if (calc3c(i)){
            console.log("Fizz");
        }
        else if (calc5a(i)){
            console.log("Buzz");
        }
        else{
            console.log(i);
        }
    }
}

fzbz(100);

```
