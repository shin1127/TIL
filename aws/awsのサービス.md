# AWSのサービス

## EC2

# ストレージサービス

## S3
Amazon Simple Storage Service  
ファイルを保存してくれるサービス  
書き込みや読み出しがS3よりさらに遅いけど、安いサービスもある(Amazon S3 Glacier)

## EBS
Amazon Elastic Brock Store  
S3よりも高速なデータ読み込み、書き出しが可能なブロックストレージサービス

その他：EFS(Amazon Elastic File System)

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

