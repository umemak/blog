---
title: "MML仕様"
date: "2022-02-02"

---

それなりになってきたので、文法的なところもちゃんと決めていきたい。

MMLの標準化がされていないのは前に調べた通りなので、仕方ない。

| 記号 | 意味 | 備考 |
| --- | --- | --- |
| cdefgab | 音階 |  |
| +, # | 半音上げ | 音階の直後に書く |
| - | 半音下げ | 音階の直後に書く |
| . | 符点 | |
| ^ | タイ | |
| r | 休符 |  |
| l | 省略時音長 | |
| o | オクターブ | |
| > | 1オクターブ上げ | |
| < | 1オクターブ下げ | |
| v | ベロシティ | 0～127 |
| @ | 音色 | 1～128 |
| $ | チャンネル | 1～16 |
| t | テンポ | 1～960 |
| p | パンポット | 0～64～127 |
| [] | 繰り返し | |
| {} | 和音 | |

こんな感じかな。
