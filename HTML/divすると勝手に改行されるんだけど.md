# divすると勝手に改行されるんだけど.md


参考：[divタグの前後で改行が入ってしまうブロック要素とインライン要素](https://qiita.com/ug23/items/4c29dc6fded65766d197)

## 原因と解決策

原因：divは改行の要素を含んでいる  
回避策：divではなくspanを利用せよ  


## 具体例

<img src="https://i.gyazo.com/7bc75a370bb899369764b43b28f97ad1.png">

```html

       <div class="workRow">
         <div class="work">
           <div id="open8" class="open">
             <h3>
               蔵書管理システム
               <span class="redcolor">(New!)</span>
             </h3>
           </div>
```

=======================================================



<img src="https://i.gyazo.com/25ee542e7f2931465409140334d64ea2.png">

```html
       <div class="workRow">
         <div class="work">
           <div id="open8" class="open">
             <h3>
               蔵書管理システム
               <div class="redcolor">(New!)</div>
             </h3>
           </div>
           <div id="mask8" class="hidden mask"></div>
           <section id="modal8" class="modal hidden">
             <p></p>
             <h3>蔵書管理システム（開発途中）</h3>
             ```
