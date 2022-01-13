---
title: "WSL2でdocker"
date: "2022-01-13"

---

WSL2でFirebaseの作業再開しようとしたら、npmやらなにやら入ってない（Surfaceのほうは過去にインストールしてたらしい）ので、
docker入れてみることにした。

https://docs.docker.com/engine/install/ubuntu/

```
$ sudo apt-get remove docker docker-engine docker.io containerd runc
$ sudo apt-get update
$ sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
$ echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
$ sudo apt-get update
$ sudo apt-get install docker-ce docker-ce-cli containerd.io
$ sudo service docker start
$ sudo docker run hello-world
```

https://docs.docker.com/engine/install/linux-postinstall/

```
$ sudo groupadd docker
$ sudo usermod -aG docker $USER
```

自動起動はとくに必要ないので省略。

で、VS Codeのremoteでcontainer開こうとしたら、dockerがないというエラー。Docker desktopインストールしないとダメなのかなぁ。。

[Docker Desktopに依存しない、WindowsでのDocker環境 - Qiita](https://qiita.com/ohtsuka1317/items/617a865b8a9d4fb67989#3-visual-studio-code-%E3%81%8B%E3%82%89%E3%81%AE%E5%88%A9%E7%94%A8)
にある通り、WSLからVS Codeを起動したらエラーなく通った。

