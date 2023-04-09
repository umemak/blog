---
title: "OpenAIのAPIを使ってみる"
date: "2023-04-09"
tags: []

---

[Whisper API, ChatGPT API, VOICEVOXを使ってAIと会話する](https://zenn.dev/umyomyomyon/articles/5f07abe67a289b)を見てやってみた。

最初実行したときに`openai.error.RateLimitError`のエラーで終了してしまい、まだ枠に余裕があるはずなのになぜ？と思ったけど、[OpenAI APIのエラー(openai.error.RateLimitError)について - Qiita](https://qiita.com/kotattsu3/items/d6533adc785ee8509e2c)によるとAPIを使うときはクレカの登録が必要らしい。

実際登録したらエラーは解消した。

VOICEBOXは前に試した時と同様、DockerのCPU版を使用。GPU版も試したけどYoga770iでは動かなかった。

で、ちょっと使ってみたけれど、何往復かしたところで音声認識をしなくなることがあった。
あとセリフが長くなりがちなので、VOICEBOXの変換待ち時間も長い。

実用にはまだハードウェアが追いついていない感じ。
