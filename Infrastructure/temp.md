# サーバとは

## Web サーバ

HTTP リクエスト-> レスポンス

## AP サーバ

Web サーバが受け付けたリクエストに応じた処理を行うためのサーバ  
（Java, Ruby などのプログラムの動作）

## DB サーバ

データベース用

## メールサーバ

## FTP サーバ

ファイルの FTP 転送のためのもの

## DNS サーバ

Domain Name System を行うためのもの  
ドメイン名と IP アドレスの対応付け、メールの宛先ホストの特定

## DHCP サーバ

Dynamic Host Configuration Protocol
ネットワーク上のデバイスに IP アドレスを割り当てる

## プロキシサーバ

クライアント PC の代わりにインターネットへ接続する

# サーバ用 OS

RedHat, CentOS, Windows Server, HP-UX

開発環境は CentOS 本番環境は RedHat が多い
RedHat->サポートあり

# ミドルウェア

Web サーバ用->Apache, Nginx, IIS など  
AP サーバ->Tomcat, WebLogic, WebSphere など  
DB サーバ->Oracle, MySQL, PostgreSQL など  
ジョブ運用-> JPI, SystemWalker

# Web 3 層構造

「Web サーバ」「AP サーバ」「DB サーバ」

# TCP/IP

TCP->接続相手を確認してからデータを送受信する（高信頼性）  
IP->相手を確認せずにデータを送受信する（高速）

# HTTP

ステートレス（状態を保持しない）、暗号化されない  
ステートレス->cookie などの技術を使って問題解決
