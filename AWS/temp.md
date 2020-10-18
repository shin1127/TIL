- データセンター = アベイラビリティゾーン
- オレゴンが一番安い、新規サービスの実装も早い

# Amazon EC2 とは

AWS において仮想サーバーを構築するサービス(Amazon Elastic Compute Cloud)  
\*Elastic: 伸縮自在な

仮想サーバー内では Linux や Windows など様々な OS を動かすことができる  
EC2 で作成された仮想サーバーをインスタンスと呼ぶ

# VPC とは

VPC: Amazon Virtual Private Cloud  
AWS においてネットワークを構成するサービス

## サブネット

> サブネット（英語: subnet）とは、IP ネットワークを論理的に細分化したもののことである[1]:1,16。1 つのネットワークを 2 つ以上のネットワークに分割することをサブネット化（subnetting）という 。  
> wikipedia

## インターネットゲートウェイ

通称 IGW

# ping コマンド

TCP/IP ネットワークで疎通を確認するのに使う  
（ちゃんと通信したら返ってくるかみたいな）

\$ ping -c 3 8.8.8.8

=====================

code:linux
dy@dy:~\$ ping -c 3 8.8.8.8 // 3 回 ping する
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=109 time=43.3 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=109 time=17.5 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=109 time=20.7 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2007ms
rtt min/avg/max/mdev = 17.463/27.161/43.280/11.475 ms

8.8.8.8 という IP アドレスを持った通信相手から 3 回応答あったことを示す
8.8.8.8→Google が運用する公開 DNS サーバーの IP アドレス

> DNS は、ホスト名（たとえば ja.wikipedia.org）の入力に対して、DNS サーバと呼ばれるコンピュータを参照し、そのホストが持つ IP アドレス（たとえば 130.94.122.197）を検索するシステムである。喩えるならば、DNS は氏名から電話番号を自動で調べる電話帳のようなものである。

IP アドレスとは
プロトコルとしての IP、そこで用いられる識別の IP アドレスがある

IP アドレス（のグローバルアドレス）はインターネット上で一意。
例：8.8.8.8 という IP アドレスはインターネット上には Google 公開 DNS サーバ以外にない
閉じたネットワーク（家庭や企業など）には重複して存在することがある（＝プライベート IP アドレス）
しかし、組織内のネットーワークにおいて全く同じアドレスが使われることはない → 通信がうまくできなくなる恐れ

パケット（データグラム）：IP でデータをやりとりするときの単位、パケットのひとつひとつにはヘッダー（IP アドレスを含む）がある

フィールド：ヘッダーの中で情報を記載する領域のこと（IP のヘッダには IP アドレスを記載するフィールドがある）

code:linux
dy@dy:~\$ ip address show
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

inet の後ろが自分のコンピューターの IP アドレス
１：や２：の後ろはネットワークインターフェイス
例　ネットワークインターフェイス io には IP アドレス 127.0.0.1 が付与されてる

IP アドレス 127.0.0.1 は自分自身を指す（＝ループバックアドレス）

    enp0s3とeth0の違いって何？

IP アドレス 10.0.2.15 は差出人に相当する

\$ transroute
=パケットがどのような道順（ルート, Route)を通って目的地まで届くのか確認するのに使う
それぞれの行はルータというネットワーク機器のことを指している
各行の IP アドレス I は、パケットが通過したルータの IP アドレス
ホップ数：行数（論理的な距離、パケットが通過するルータの台数）

// グローバル IPv4 に接続したら Apache の内容が表示される->とりあえずサーバー立ち上げは成功してそう

//test

# 参考

- Amazon Web Services ネットワーク入門
- Linux で動かしながら学ぶ TCP/IP ネットワーク入門
