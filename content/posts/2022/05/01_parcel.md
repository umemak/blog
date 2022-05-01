---
title: "Parcelを使ってみる"
date: "2022-05-01"
tags: ["JavaScript","Parcel"]

---

久しぶりにJavaScript（TypeScript）を書こうとしたら、何から始めてよいかわからなくなっていた。

あまり環境構築に手間をかけたくなかったので、[parcel-bundler/parcel: The zero configuration build tool for the web. 📦🚀](https://github.com/parcel-bundler/parcel)を使ってみた。

[Building a web app with Parcel](https://parceljs.org/getting-started/webapp/)を見ながら

```sh
npm init
npm install --save-dev parcel
```
src/index.htmlを作って、
```sh
npx parcel src/index.html
/home/umemak/workspace/mdmml_js/node_modules/@parcel/core/lib/Parcel.js:150
  #requestTracker
  ^

SyntaxError: Invalid or unexpected token
    at new Script (vm.js:83:7)
    at NativeCompileCache._moduleCompile (/home/umemak/workspace/mdmml_js/node_modules/v8-compile-cache/v8-compile-cache.js:240:18)
    at Module._compile (/home/umemak/workspace/mdmml_js/node_modules/v8-compile-cache/v8-compile-cache.js:184:36)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:789:10)
    at Module.load (internal/modules/cjs/loader.js:653:32)
    at tryModuleLoad (internal/modules/cjs/loader.js:593:12)
    at Function.Module._load (internal/modules/cjs/loader.js:585:3)
    at Module.require (internal/modules/cjs/loader.js:692:17)
    at require (/home/umemak/workspace/mdmml_js/node_modules/v8-compile-cache/v8-compile-cache.js:159:20)
    at Object.<anonymous> (/home/umemak/workspace/mdmml_js/node_modules/@parcel/core/lib/index.js:81:39)
/home/umemak/workspace/mdmml_js/node_modules/@parcel/logger/lib/Logger.js:41
  #logEmitter
  ^

SyntaxError: Invalid or unexpected token
    at new Script (vm.js:83:7)
    at NativeCompileCache._moduleCompile (/home/umemak/workspace/mdmml_js/node_modules/v8-compile-cache/v8-compile-cache.js:240:18)
    at Module._compile (/home/umemak/workspace/mdmml_js/node_modules/v8-compile-cache/v8-compile-cache.js:184:36)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:789:10)
    at Module.load (internal/modules/cjs/loader.js:653:32)
    at tryModuleLoad (internal/modules/cjs/loader.js:593:12)
    at Function.Module._load (internal/modules/cjs/loader.js:585:3)
    at Module.require (internal/modules/cjs/loader.js:692:17)
    at require (internal/modules/cjs/helpers.js:25:18)
    at _logger (/home/umemak/workspace/mdmml_js/node_modules/parcel/lib/cli.js:54:16)
```
うーん。。めんどくさい。。
