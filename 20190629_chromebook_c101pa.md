# C101PA届いた

* 起動直後はOSが古い→ChromeOSバージョンアップ実施
* Googleアンケートアプリが対応していない
* Kindleアプリインストールできた
* 全体的にC224NA比べて遅い（知ってた）
* 今回は開発者モードにしないで普通にLinux有効化した
* brewインストール
```
$ sh -c "$(curl -fsSL https://raw.githubusercontent.com/Linuxbrew/install/master/install.sh)"
$ test -d ~/.linuxbrew && PATH="$HOME/.linuxbrew/bin:$HOME/.linuxbrew/sbin:$PATH"
$ test -d /home/linuxbrew/.linuxbrew && PATH="/home/linuxbrew/.linuxbrew/bin:/home/linuxbrew/.linuxbrew/sbin:$PATH"
$ test -r ~/.bash_profile && echo "export PATH='$(brew --prefix)/bin:$(brew --prefix)/sbin'":'"$PATH"' >>~/.bash_profile
$ echo "export PATH='$(brew --prefix)/bin:$(brew --prefix)/sbin'":'"$PATH"' >>~/.profile
$ Homebrew 2.1.6
Homebrew/linuxbrew-core (git revision bb5a; last commit 2019-06-29)
```
