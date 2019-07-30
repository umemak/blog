# Chromebook(C101PA)にVSCodeをインストールする２

昨日は空き容量が足りなくなってあきらめたので、今回は何もない状態からやってみる。

## インストールしながら空き容量をチェック
  * Linuxを再インストールした直後
    ```
    $ df -h
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vdb        5.5G  1.3G  3.9G  25% /
    ```

  * VSCodeのインストールしてdebファイル削除したあと
    ```
    $ df -h
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vdb        5.5G  1.8G  3.4G  34% /
    ```

  * mozcインストール後
    ```
    $ df -h
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vdb        5.5G  2.1G  3.1G  42% /
    ```

  * fonts-notoインストール後
    ```
    $ df -h
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vdb        5.5G  2.2G  3.0G  42% /
    ```

  * 1GB程度消費する模様

## https://qiita.com/kukita/items/b673bf6eba2cc91fc545 に沿ってGoもインストールする
  * goインストール後
    ```
    $ df -h
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vdb        5.5G  2.6G  2.7G  50% /
    ```

無事インストールできた。先人の知恵に感謝。
