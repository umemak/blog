---
title: "podman desktop"
date: "2023-04-08"
tags: []

---

[Podman Desktop - Containers and Kubernetes | Podman Desktop](https://podman-desktop.io/)

Yoga770i、まだコンテナ環境入れてなかったので、今回はpodmanを使ってみることにした。

podman desktopをインストールしただけではコンテナは使えず、podmanをインストールする必要がある。

podmanをインストールするには、Virtual Machine Platformを有効化する必要がある。

Powershellを管理者権限で起動して、以下コマンドを実行。
```sh
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```
[Manual installation steps for older versions of WSL | Microsoft Learn](https://learn.microsoft.com/en-us/windows/wsl/install-manual#step-3---enable-virtual-machine-feature)

WSL2のインストールも必要。。

Powershellを管理者権限で起動して、以下コマンドを実行。
```sh
wsl --install
```

これでpodmanがインストールできた。が起動しない。WSLをインストールした後OS再起動が必要。

うーん、WSL2インストールする必要があるなら、あえてpodman使う必要ないかなー。
