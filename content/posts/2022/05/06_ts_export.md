---
title: "TypeScriptのexport"
date: "2022-05-06"
tags: ["TypeScript"]

---

MDMMLのTypeScript移植が大体できたので、HTMLから呼び出せるようにしたい。

先日はexportしてるはずなのに見つからないというエラーでどうしたら良いかわからず。

[HTMLから外部のJavascriptファイルのfunctionを呼びたい](https://teratail.com/questions/190709)はやりたいこととあっているように思える。

```ts
interface Window { Hello(): void; }
declare var window: Window;
window.Hello = () => {
    console.log(Buffer.from(MDtoSMF("cdefg")).toString("binary"));
};
```

としてみたら呼べたけれど、今度は`Buffer is not defined`だと。

いろいろやってみて、
```ts
import { MDtoSMF } from './mdmml';

interface Window { MDtoSMF(md: string): ArrayBuffer; }
declare var window: Window;
window.MDtoSMF = (md: string) => {
    return MDtoSMF(md);
};
```
これで動いた。正しい自信はない。。

