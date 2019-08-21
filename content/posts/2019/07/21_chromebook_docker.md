# Chromebookにdockerインストール

## 環境
* C101PA

## 手順
* [公式の手順](https://docs.docker.com/install/linux/docker-ce/debian/#install-using-the-repository)に従う
  ```
  $ sudo apt-get update
  $ sudo apt-get install \
      apt-transport-https \
      ca-certificates \
      curl \
      gnupg2 \
      software-properties-common -y
  $ curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
  $ sudo apt-key fingerprint 0EBFCD88
  $ sudo add-apt-repository \
     "deb [arch=arm64] https://download.docker.com/linux/debian \
     $(lsb_release -cs) \
     stable"
  $ sudo apt-get update
  $ sudo apt-get install docker-ce docker-ce-cli containerd.io -y
  $ sudo docker run hello-world
  ```
  できた。
