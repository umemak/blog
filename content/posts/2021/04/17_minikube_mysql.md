---
title: "WindowsのminikubeでMySQLを動かす"
date: "2021-04-17"
tags: ["windows","minikube","mysql"]
---

MacでやったらMySQLの起動時にエラーで落ちてしまったので、Windowsでどうなるか試す。

基本的には公式のドキュメントを参照。
https://kubernetes.io/ja/docs/tasks/run-application/run-single-instance-stateful-application/

## munikubeインストール

```
winget install minikube
```

## minikube起動

```
minikube start
```

```
$ kubectl get nodes
NAME       STATUS   ROLES                  AGE   VERSION
minikube   Ready    control-plane,master   73s   v1.20.2
```

## マニフェストファイル作成

[mysql.yaml](./mysql.yaml)

## デプロイ

```
$ kubectl apply -f mysql.yaml 
service/mysql created
deployment.apps/mysql created
persistentvolumeclaim/mysql-pv-claim created
persistentvolume/mysql-pv-volume created
```

```
$ kubectl get pods -l app=mysql
NAME                     READY   STATUS    RESTARTS   AGE
mysql-68579b78bb-qcqww   1/1     Running   0          5m33s
```

動いてるねぇ。。

## 後片付け

```
$ kubectl.exe delete -f mysql.yaml
service "mysql" deleted
deployment.apps "mysql" deleted
persistentvolumeclaim "mysql-pv-claim" deleted
persistentvolume "mysql-pv-volume" deleted
$ minikube stop
```

Macのほう、MySQLのコマンドライン色々指定したのがまずかったのかなぁ。

それはそれとして、Surface go 2でminikubeは重すぎて実用的ではない。

