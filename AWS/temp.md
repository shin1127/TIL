- データセンター = アベイラビリティゾーン
- オレゴンが一番安い、新規サービスの実装も早い

# Amazon EC2とは

AWSにおいて仮想サーバーを構築するサービス(Amazon Elastic Compute Cloud)  
*Elastic: 伸縮自在な

仮想サーバー内ではLinuxやWindowsなど様々なOSを動かすことができる  
EC2で作成された仮想サーバーをインスタンスと呼ぶ  

# VPCとは

VPC: Amazon Virtual Private Cloud  
AWSにおいてネットワークを構成するサービス



## サブネット

> サブネット（英語: subnet）とは、IPネットワークを論理的に細分化したもののことである[1]:1,16。1つのネットワークを2つ以上のネットワークに分割することをサブネット化（subnetting）という 。  
> wikipedia

## インターネットゲートウェイ

通称IGW

# pingコマンド

TCP/IPネットワークで疎通を確認するのに使う  
（ちゃんと通信したら返ってくるかみたいな）

$ ping -c 3 8.8.8.8


=====================

code:linux
 dy@dy:~$ ping -c 3 8.8.8.8  // 3回pingする
 PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
 64 bytes from 8.8.8.8: icmp_seq=1 ttl=109 time=43.3 ms
 64 bytes from 8.8.8.8: icmp_seq=2 ttl=109 time=17.5 ms
 64 bytes from 8.8.8.8: icmp_seq=3 ttl=109 time=20.7 ms
 
 --- 8.8.8.8 ping statistics ---
 3 packets transmitted, 3 received, 0% packet loss, time 2007ms
 rtt min/avg/max/mdev = 17.463/27.161/43.280/11.475 ms

8.8.8.8というIPアドレスを持った通信相手から3回応答あったことを示す
8.8.8.8→Googleが運用する公開DNSサーバーのIPアドレス

> DNSは、ホスト名（たとえばja.wikipedia.org）の入力に対して、DNSサーバと呼ばれるコンピュータを参照し、そのホストが持つIP アドレス（たとえば130.94.122.197）を検索するシステムである。喩えるならば、DNSは氏名から電話番号を自動で調べる電話帳のようなものである。

IPアドレスとは
プロトコルとしてのIP、そこで用いられる識別のIPアドレスがある

IPアドレス（のグローバルアドレス）はインターネット上で一意。
例：8.8.8.8というIPアドレスはインターネット上にはGoogle公開DNSサーバ以外にない
閉じたネットワーク（家庭や企業など）には重複して存在することがある（＝プライベートIPアドレス）
しかし、組織内のネットーワークにおいて全く同じアドレスが使われることはない→通信がうまくできなくなる恐れ

パケット（データグラム）：IPでデータをやりとりするときの単位、パケットのひとつひとつにはヘッダー（IPアドレスを含む）がある

フィールド：ヘッダーの中で情報を記載する領域のこと（IPのヘッダにはIPアドレスを記載するフィールドがある）

code:linux
 dy@dy:~$ ip address show
 1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
     link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
     inet 127.0.0.1/8 scope host lo
        valid_lft forever preferred_lft forever
     inet6 ::1/128 scope host 
        valid_lft forever preferred_lft forever
 2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
     link/ether 08:00:27:d4:17:4a brd ff:ff:ff:ff:ff:ff
     inet 10.0.2.15/24 brd 10.0.2.255 scope global dynamic noprefixroute enp0s3
        valid_lft 53899sec preferred_lft 53899sec
     inet6 fe80::ac32:a36e:7955:7354/64 scope link noprefixroute 
        valid_lft forever preferred_lft forever
 

inetの後ろが自分のコンピューターのIPアドレス
１：や２：の後ろはネットワークインターフェイス
例　ネットワークインターフェイスioにはIPアドレス127.0.0.1が付与されてる

IPアドレス127.0.0.1は自分自身を指す（＝ループバックアドレス）

	enp0s3とeth0の違いって何？

IPアドレス10.0.2.15は差出人に相当する

$ transroute
=パケットがどのような道順（ルート, Route)を通って目的地まで届くのか確認するのに使う
それぞれの行はルータというネットワーク機器のことを指している
各行のIPアドレスIは、パケットが通過したルータのIPアドレス
ホップ数：行数（論理的な距離、パケットが通過するルータの台数）



# 参考
- Amazon Web Servicesネットワーク入門
- Linuxで動かしながら学ぶTCP/IPネットワーク入門