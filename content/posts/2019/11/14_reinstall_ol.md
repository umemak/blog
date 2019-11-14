---
title: "Oracle Linux再セットアップ"
date: "2019-11-14"
tags: ["oracle"]
---

mattermostが動かないのは、素のyumでインストールしたdockerのバージョンが古いことが原因の可能性があるので、最新版に入れ直す。

素で入れた方のバージョン
```Bash
$ docker --version
Docker version 18.09.8-ol, build 76804b7
```

既存の環境でやるのはまた何が起こるかわからないので、インスタンスを再作成してやり直す。

手順
https://docs.docker.com/install/linux/docker-ce/centos/

```Bash
$ sudo yum update -y
$ docker --version
-bash: docker: command not found
$ sudo yum install -y yum-utils \
  device-mapper-persistent-data \
  lvm2
$ sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
$ sudo yum install docker-ce docker-ce-cli containerd.io
$ docker --version
Docker version 19.03.4, build 9013bf583a
$ sudo systemctl start docker
$ sudo usermod -aG docker opc
# 再ログイン
$ docker run hello-world
docker: Error response from daemon: OCI runtime create failed: container_linux.go:346: starting container process caused "process_linux.go:449: container init caused \"write /proc/self/attr/keycreate: permission denied\"": unknown.
ERRO[0000] error waiting for container: context canceled 
# https://stackoverflow.com/questions/56870478/cannot-start-docker-container-in-docker-ce-on-oracle-linux
$ sudo yum install http://mirror.centos.org/centos/7/extras/x86_64/Packages/container-selinux-2.107-1.el7_6.noarch.rpm
$ docker run hello-world

Hello from Docker!
```
OK。
続いてmattermostのセットアップ

手順
https://github.com/mattermost/mattermost-docker
```bash
$ sudo yum install git docker-compose -y
$ git clone https://github.com/mattermost/mattermost-docker.git
$ cd mattermost-docker
$ docker-compose build
$ mkdir -p ./volumes/app/mattermost/{data,logs,config,plugins}
$ sudo chown -R 2000:2000 ./volumes/app/mattermost/
$ docker-compose up
```
