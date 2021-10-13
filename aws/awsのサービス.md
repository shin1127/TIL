# AWSのサービス




## AMI
Amazon Machine Image  
1つのAMIから（同じ設定の）複数のインスタンスを起動できる

## Athena
S3内のデータをSQLクエリを使って分析できる

## Amazon Cognito

## CloudFront
利用者にハイスピードでコンテンツを提供するサービス  
利用者から一番近いエッジサーバーからコンテンツを提供する  
CloudFront自体は無料枠あるけど、EC2やS3といったサービスに対して通信料はしっかり請求されるので注意

## CloudWatch Logs 

## AWS Config




## EC2

## インスタンスストア
https://docs.aws.amazon.com/ja_jp/AWSEC2/latest/UserGuide/InstanceStorage.html

## Amazon EMR


# ストレージサービス

## S3
Amazon Simple Storage Service  
ファイルを保存してくれるサービス  
書き込みや読み出しがS3よりさらに遅いけど、安いサービスもある(Amazon S3 Glacier)  
特に設定していなくてもリージョンに設置される（＝複数のアベイラビリティゾーンに自動的に保存される）

特に設定していなくとも、自動でスケーリングされる

## Amazon S3 Transfer Acceleration 


## EBS
Amazon Elastic Brock Store  
S3よりも高速なデータ読み込み、書き出しが可能なブロックストレージサービス  
スナップショットを使ってバックアップが可能


その他：EFS(Amazon Elastic File System)

## EFS
EC2インスタンスからつなげることができるNAS

## ELB
ロードバランサー

## IAM
AWS Identify and Access Management  
ユーザ管理に関わるサービス


##  Kinesis


##  AWS GuardDuty

# ネットワークサービス

## VPC
Amazon Virtual Private Cloud  
プライベートIPアドレスを割り当てたネットワークに仮想VPNゲートウェイを用意して、  
社内ネットワーク側のVPNゲートウェイとIPsecによる暗号化通信を行うことで、拠点間インターネットVPNを構築する

セキュリティグループというもので送信・受信ポリシーを設定することで、仮想サーバーへのアクセス制御が行える
(AmazonRDSに接続するときに、接続を許可するのはAmazon EC2インスタンスだけとする！みたいなときに  
なんかやった記憶あるわ)

## Route53
DNSを運用管理するシステム

# データベースサービス

## RDS
RDBMS(Relational Database Management System)  
MySQL, PostgraSQLは無料、OracleやMycrosoft SQL serverとかは有料  

ライセンスをクラウドサービスへ持ち込めること：BYOL（Bring Your Own License）  

その他、AWS独自開発のAmazon Auroraとかもある（AWSのサービスと併用するならめちゃ強力ってマックのJKがいってた）  

## Redshift
ペタバイト（1024テラバイト）クラスのデータを処理できるサービス  

## AWS Shield
DDoS攻撃に対する保護サービス

## SnowBall Edge
大量のデータをAWSにアップロードするときに使うアナログっぽいサービス  
堅牢なアタッシュケースにハードディスクを入れて、データセンターに配送する  

## SNS
Simple Notification Service
* Notification : 通知
メッセージ配信サービス

## SQS
キューの処理

## NoSQL
AWS独自開発：Amazon DynamoDB  
高速で拡張に優れる

# データ分析、IoT

AWS IoT, AWS IoT SiteWisem Amazon Timestream, AWS IoT Events  

# AI, 機械学習

ユーザーが機械学習を行うサービスと、学習済みサービスの2種類がある

## ユーザーが機械学習を行う

Amazon SageMakerなど  
ユーザーが独自にモデルを構築できるので応用分野が広い  

一方で、データ分析可能な人材確保が必要になるので挑戦難易度が高い

## 学習済みモデル
例：音声認識、画像認識、自然言語処理、自動翻訳、動画認識・分析などをAPI経由で提供  

## リードレプリカ
https://pfs.nifcloud.com/navi/tech/read_replicas.htm
