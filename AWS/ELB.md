> 3. ALBとELBの違い？初心者にもわかりやすく解説
AWSでALBを利用する場合、よく一緒にされるのがELBという言葉です。
ELBとは「Elastic Load Balancing」の略称で、元々はこのELBがAWSにおけるロードバランシングサービスでした。
しかしのちにALBが追加オプションとして開発された際に、ELBはその名称を「Classic Load Balancer（CLB）」に変えることになります。
そしてALBとCLBのサービスをまとめた総称として、ELBが使われるようになったのです。
さらに今ではNetwork Load Balancer（NLB）も追加され、その内容がさらに充実しています。
つまりELBとは、ALB、CLB、NLBという3種類の魅力的なロードバランサーを持つAWSのロードバランシングサービスの総称のことなのです。
ALBはCLBと比べるとさまざまな面で特徴的な部分があり、ALBならではの魅力といったものが備わっています。
例えば以下のような点は、ALBの特徴となっています。
・レイヤー7(アプリケーションレイヤー)での動作
・新たにWebSocket とHTTP/2をサポート
・最新のアプリケーションアーキテクチャを対象
・ターゲットグループにルーティングが行える
・複数のアベイラビリティーゾーンの利用

https://www.wafcharm.com/blog/difference-between-alb-and-elb/
