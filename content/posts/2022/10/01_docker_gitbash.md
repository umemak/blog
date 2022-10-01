---
title: "GitBashでDockerでMount"
date: "2022-10-01"
tags: ["gitbash", "docker"]

---

WSL2が不安定なので、開発環境をGitBash使うようにして、おおむね問題なかったのだが、Dockerでローカルをマウントして使うときに問題が。

OpenAPIのコード生成するときに
```sh
docker run --rm \
  -v ${PWD}:/local openapitools/openapi-generator-cli generate \
  -i /local/openapi.yml \
  -g go-server \
  --additional-properties=router=chi,featureCORS=true \
  -o /local/out
```
だと
```sh
[error] The spec file is not found: C:/Program Files/Git/local/openapi.yml
[error] Check the path of the OpenAPI spec and try again.
```
こんなエラーになる。

[Mount volume doesn't work on Windows 10 using git-bash · Issue #673 · docker-archive/toolbox](https://github.com/docker-archive/toolbox/issues/673)を参考に、`MSYS_NO_PATHCONV=1`をつけたら動いた。
```sh
MSYS_NO_PATHCONV=1 docker run --rm \
  -v ${PWD}:/local openapitools/openapi-generator-cli generate \
  -i /local/openapi.yml \
  -g go-server \
  --additional-properties=router=chi,featureCORS=true \
  -o /local/out
```
