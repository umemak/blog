# ChromeBook(C223NA)にVSCodeをインストールする

C101PAで一通りできたのでインテルCPUの機種でもやってみる

* インストール開始
  ```
  $ df -h
  Filesystem      Size  Used Avail Use% Mounted on
  /dev/vdb         18G  1.2G   15G   8% /
  ```
  広い

* aptの設定追加はしていない
  * golang-1.11 が見つからなかったので設定追加した

* VSCodeのパッケージファイルは公式から取得

* fonts-notoまでインストール終わった時点での消費
  ```
  $ df -h
  Filesystem      Size  Used Avail Use% Mounted on
  /dev/vdb         18G  1.7G   15G  11% /
  ```
  C101PAのときより消費が少ない

* golangともろもろ拡張機能インストール
  ```
  $ df -h
  Filesystem      Size  Used Avail Use% Mounted on
  /dev/vdb         18G  2.4G   14G  15% /
  ```
  余裕。
  C101PAでインストールできなかった`dlv`も入った。

* dockerインストール
  ```
  $ df -h
  Filesystem      Size  Used Avail Use% Mounted on
  /dev/vdb         18G  3.0G   13G  19% /
  ```
  VSCodeのremoteも入った！
