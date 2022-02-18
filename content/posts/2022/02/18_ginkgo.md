---
title: "Ginkgoわからん"
date: "2022-02-18"

---

MDMMLじゃない話。

[https://onsi.github.io/ginkgo/](https://onsi.github.io/ginkgo/) でテストを、
```
Describe(){
    Context(){
        // 準備
        It(){
            Expect()
        }
        // 次の準備
        It(){
            Expect()
        }
        // 後片付け
    }
}
```
みたいな感じで書いていたら、思った通りの動きにならなくてハマった。

どうやら、Contextの中は上から順番に実行されるのではなく、
```
Describe(){
    Context(){
        // 準備
        // 次の準備
        // 後片付け
        It(){
            Expect()
        }
        It(){
            Expect()
        }
    }
}
```
となるらしい。

やりたい順番で実行したければ、
```
Describe(){
    It(){
        // 準備
        Expect()
        // 次の準備
        Expect()
        // 後片付け
    }
}
```
ってやらないといけないのかなぁ。

いまいち作法がわからない。そもそもこういうシナリオ的なテストに使うものではないのでは？という気もしてきた。
