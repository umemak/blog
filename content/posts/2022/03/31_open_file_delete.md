---
title: "開いたままのファイルを削除したらどうなるか2"
date: "2022-03-31"
tags: ["linux"]

---

昨日のCパターンを実際にAWSで試してみた。Docker関係なかった。

- `Amazon Linux 2 AMI (HVM) - Kernel 5.10, SSD Volume Type`と`Microsoft Windows Server 2019 Base`のインスタンスを`t2.micro`でそれぞれ作成
- Linux側からWindows側へのセキュリティグループからのアクセスを許可

### Windows側

- C:\Users\shared を作成してプロパティから共有設定

### Linux側

- Windowsの共有フォルダをマウントしてテスト用ファイル作成
```
$ sudo yum install cifs-utils
$ sudo mkdir /mnt/shared
$ sudo mount -t cifs //<WindowsのIP>/Users/shared /mnt/shared -o user=Administrator
$ ls /mnt/shared/
$ sudo mkdir /mnt/shared/test
$ sudo vi /mnt/shared/test/test.txt
```

- Goのインストールとオープンして待機するプログラムの実行
```
$ sudo su
# rm -rf /usr/local/go && tar -C /usr/local -xzf go1.18.linux-amd64.tar.gz
# exit
$ export PATH=$PATH:/usr/local/go/bin
$ go version
go version go1.18 linux/amd64
$ sudo yum install git
$ git clone https://github.com/umemak/open_file_delete_test.git
$ cd open_file_delete_test
$ sudo /usr/local/go/bin/go run main.go /mnt/shared/test/test.txt
```

- Linux側別コンソールでファイル削除など確認
```
$ sudo lsof | grep test.txt
main      3916                root    3r      REG               0,40         7 1688849860265148 /mnt/shared/test/test.txt
main      3916 3917           root    3r      REG               0,40         7 1688849860265148 /mnt/shared/test/test.txt
main      3916 3918           root    3r      REG               0,40         7 1688849860265148 /mnt/shared/test/test.txt
main      3916 3919           root    3r      REG               0,40         7 1688849860265148 /mnt/shared/test/test.txt
$ ls -l /mnt/shared/test/
total 1
-rwxr-xr-x 1 root root 7 Mar 31 04:51 test.txt

$ sudo rm /mnt/shared/test/test.txt
$ sudo lsof | grep test.txt
main      3916                root    3r      REG               0,40         7 1688849860265148 /mnt/shared/test/test.txt (deleted)
main      3916 3917           root    3r      REG               0,40         7 1688849860265148 /mnt/shared/test/test.txt (deleted)
main      3916 3918           root    3r      REG               0,40         7 1688849860265148 /mnt/shared/test/test.txt (deleted)
main      3916 3919           root    3r      REG               0,40         7 1688849860265148 /mnt/shared/test/test.txt (deleted)

$ ls -l /mnt/shared/test/
total 1
-rwxr-xr-x 0 root root 7 Mar 31 04:51 test.txt

$ cat /mnt/shared/test/test.txt 
cat: /mnt/shared/test/test.txt: No such file or directory
```

- Goプログラム終了
```
$ ls -l /mnt/shared/test/
total 0
```
