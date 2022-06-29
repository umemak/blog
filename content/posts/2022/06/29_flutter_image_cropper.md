---
title: "Image Cropper"
date: "2022-06-29"
tags: ["Flutter"]

---

アップロードする画像を正方形にしたかったので、加工用のパッケージを入れてみた。

[hnvn/flutter_image_cropper: A Flutter plugin for Android and iOS supports cropping images](https://github.com/hnvn/flutter_image_cropper)

これがFlutter Webだとどうもうまく動かない。

```
croppie_dart.dart:129 Uncaught (in promise) TypeError: dart.global.Croppie is not a constructor
    at new croppie_dart._Croppie.new (croppie_dart.dart:129:50)
    at Croppie.new (croppie_dart.dart:68:12)
    at cropImage (image_cropper_for_web.dart:120:21)
    at cropImage.next (<anonymous>)
    at runBody (async_patch.dart:84:54)
    at Object._async [as async] (async_patch.dart:123:5)
    at image_cropper_for_web.ImageCropperPlugin.new.cropImage (image_cropper_for_web.dart:74:33)
    at cropper.ImageCropper.new.cropImage (cropper.dart:86:21)
    at NewPostPage.dart:206:52
```

Flutter、まだわからないことが多い。。
