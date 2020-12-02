# windows にとっての touch コマンド.md

~~copy null コマンドによって 0 バイトファイルを生成できる~~

PowerShell と CMD ではコマンドが異なる

PowerShell では  
$ New-Item bar.txt  
CMD では  
$ copy nul foo.txt  
$ type nul > foo.txt  
