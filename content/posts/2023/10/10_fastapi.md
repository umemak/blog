---
title: "FastAPI入門2"
date: "2023-10-10"
tags: ["FastAPI"]

---

昨日の続き。テストを流した時のエラーは、参考にしたサイトのものと一部バージョンが変わっているのが原因らしく。

[pytest-asyncio のモードのデフォルト値が変わったよ＆出戻りのご連絡｜基幹システムのクラウド移行・構築・導入支援のBeeX](https://www.beex-inc.com/blog/rejoin-nasu)

を参考に`@pytest.fixture`を`@pytest_asyncio.fixture`に変更したら解消した。

他にもwarningがいくつか出ていたので、併せて修正していったが、

> PydanticDeprecatedSince20: Using extra keyword arguments on `Field` is deprecated and will be removed. Use `json_schema_extra` instead. (Extra keys: 'example'). Deprecated in Pydantic V2.0 to be removed in V3.0. See Pydantic V2 Migration Guide at https://errors.pydantic.dev/2.4/migration/

の直し方がよくわからない。
