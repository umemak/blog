---
title: "GoReleaser"
date: "2023-01-24"
tags: ["go"]

---

[GoReleaser - GoReleaser](https://goreleaser.com/)使ってみた。

うまく動かなかった。

```sh
$ go install github.com/goreleaser/goreleaser@latest
$ goreleaser init
$ goreleaser release --snapshot --rm-dist
  • starting release...
  • loading config file                              file=.goreleaser.yaml
  • loading environment variables
  • getting and validating git state
    • ignoring errors because this is a snapshot     error=git doesn't contain any tags. Either add a tag or use --snapshot
    • building...                                    commit=c555bfd95c67f41425d8155510f376d0015665eb latest tag=v0.0.0
    • pipe skipped                                   reason=disabled during snapshot mode
  • parsing tag
  • setting defaults
  • running before hooks
    • running                                        hook=go mod tidy
    • running                                        hook=go generate ./...
    • took: 6s
  • snapshotting
    • building snapshot...                           version=0.0.1-next
  • checking distribution directory
  • loading go mod information
  • build prerequisites
  • writing effective config file
    • writing                                        config=dist\config.yaml
  • building binaries
    • building                                       binary=dist\asin2md_linux_386\asin2md
    • building                                       binary=dist\asin2md_linux_amd64_v1\asin2md
    • building                                       binary=dist\asin2md_windows_amd64_v1\asin2md.exe
    • building                                       binary=dist\asin2md_darwin_amd64_v1\asin2md
    • building                                       binary=dist\asin2md_linux_arm64\asin2md
    • building                                       binary=dist\asin2md_windows_arm64\asin2md.exe
    • building                                       binary=dist\asin2md_darwin_arm64\asin2md
    • building                                       binary=dist\asin2md_windows_386\asin2md.exe
  ⨯ release failed after 6s                  error=build for asin2md does not contain a main function
Learn more at https://goreleaser.com/errors/no-main
```
[ドキュメント](https://goreleaser.com/errors/no-main/#if-your-maingo-is-not-in-the-root-folder)によると、mainパッケージがルート以外のときはパスを指定しないといけないらしい。

```yaml
builds:
  - 
    main: ./cmd/asin2md
    env:
      - CGO_ENABLED=0
    goos:
      - linux
      - windows
      - darwin
```

再実行
```sh
$ goreleaser release --snapshot --rm-dist
  • starting release...
  • loading config file                              file=.goreleaser.yaml
  • loading environment variables
  • getting and validating git state
    • ignoring errors because this is a snapshot     error=git doesn't contain any tags. Either add a tag or use --snapshot
    • building...                                    commit=c555bfd95c67f41425d8155510f376d0015665eb latest tag=v0.0.0
    • pipe skipped                                   reason=disabled during snapshot mode
  • parsing tag
  • setting defaults
  • running before hooks
    • running                                        hook=go mod tidy
    • running                                        hook=go generate ./...
    • took: 1s
  • snapshotting
    • building snapshot...                           version=0.0.1-next
  • checking distribution directory
    • --rm-dist is set, cleaning it up
  • loading go mod information
  • build prerequisites
  • writing effective config file
    • writing                                        config=dist\config.yaml
  • building binaries
    • building                                       binary=dist\asin2md_windows_amd64_v1\asin2md.exe
    • building                                       binary=dist\asin2md_darwin_arm64\asin2md
    • building                                       binary=dist\asin2md_windows_arm64\asin2md.exe
    • building                                       binary=dist\asin2md_linux_amd64_v1\asin2md
    • building                                       binary=dist\asin2md_windows_386\asin2md.exe
    • building                                       binary=dist\asin2md_darwin_amd64_v1\asin2md
    • building                                       binary=dist\asin2md_linux_arm64\asin2md
    • building                                       binary=dist\asin2md_linux_386\asin2md
    • took: 1m35s
  • archives
    • creating                                       archive=dist\asin2md_Windows_x86_64.zip
    • creating                                       archive=dist\asin2md_Linux_x86_64.tar.gz
    • creating                                       archive=dist\asin2md_Darwin_arm64.tar.gz
    • creating                                       archive=dist\asin2md_Windows_i386.zip
    • creating                                       archive=dist\asin2md_Windows_arm64.zip
    • creating                                       archive=dist\asin2md_Darwin_x86_64.tar.gz
    • creating                                       archive=dist\asin2md_Linux_arm64.tar.gz
    • creating                                       archive=dist\asin2md_Linux_i386.tar.gz
    • took: 1s
  • calculating checksums
  • storing release metadata
    • writing                                        file=dist\artifacts.json
    • writing                                        file=dist\metadata.json
  • release succeeded after 1m37s
```
できた。

GITHUB_TOKEN作ってexportして、`.gitignore`と`.golereaser.yaml`をcommit&pushしてから（重要）タグをつけて`goreleaser release`実行。

```sh
$ goreleaser release --rm-dist
  • starting release...
  • loading config file                              file=.goreleaser.yaml
  • loading environment variables
    • using token from "$GITHUB_TOKEN"
  • getting and validating git state
    • building...                                    commit=c082a00c058117d03f42f1fa22d57e3175437c20 latest tag=v0.1.1
    • took: 1s
  • parsing tag
  • setting defaults
  • running before hooks
    • running                                        hook=go mod tidy
    • running                                        hook=go generate ./...
    • took: 1s
  • checking distribution directory
    • --rm-dist is set, cleaning it up
  • loading go mod information
  • build prerequisites
  • writing effective config file
    • writing                                        config=dist\config.yaml
  • building binaries
    • building                                       binary=dist\asin2md_darwin_arm64\asin2md
    • building                                       binary=dist\asin2md_linux_amd64_v1\asin2md
    • building                                       binary=dist\asin2md_linux_arm64\asin2md
    • building                                       binary=dist\asin2md_linux_386\asin2md
    • building                                       binary=dist\asin2md_windows_amd64_v1\asin2md.exe
    • building                                       binary=dist\asin2md_windows_386\asin2md.exe
    • building                                       binary=dist\asin2md_windows_arm64\asin2md.exe
    • building                                       binary=dist\asin2md_darwin_amd64_v1\asin2md
    • took: 8s
  • generating changelog
    • writing                                        changelog=dist\CHANGELOG.md
  • archives
    • creating                                       archive=dist\asin2md_Windows_arm64.zip
    • creating                                       archive=dist\asin2md_Linux_x86_64.tar.gz
    • creating                                       archive=dist\asin2md_Darwin_x86_64.tar.gz
    • creating                                       archive=dist\asin2md_Windows_x86_64.zip
    • creating                                       archive=dist\asin2md_Windows_i386.zip
    • creating                                       archive=dist\asin2md_Darwin_arm64.tar.gz
    • creating                                       archive=dist\asin2md_Linux_i386.tar.gz
    • creating                                       archive=dist\asin2md_Linux_arm64.tar.gz
    • took: 2s
  • calculating checksums
  • publishing
    • scm releases
      • creating or updating release                 repo=umemak/asin2md tag=v0.1.1
      • release created                              name=v0.1.1 release-id=90022528 request-id=F08E:0435:2A740:30C56:63CFB390
      • uploading to release                         file=dist\asin2md_Darwin_x86_64.tar.gz name=asin2md_Darwin_x86_64.tar.gz
      • uploading to release                         file=dist\asin2md_Windows_i386.zip name=asin2md_Windows_i386.zip
      • uploading to release                         file=dist\asin2md_Darwin_arm64.tar.gz name=asin2md_Darwin_arm64.tar.gz
      • uploading to release                         file=dist\asin2md_Windows_arm64.zip name=asin2md_Windows_arm64.zip
      • uploading to release                         file=dist\asin2md_Linux_arm64.tar.gz name=asin2md_Linux_arm64.tar.gz
      • uploading to release                         file=dist\asin2md_Linux_i386.tar.gz name=asin2md_Linux_i386.tar.gz
      • uploading to release                         file=dist\asin2md_Linux_x86_64.tar.gz name=asin2md_Linux_x86_64.tar.gz
      • uploading to release                         file=dist\asin2md_Windows_x86_64.zip name=asin2md_Windows_x86_64.zip
      • uploading to release                         file=dist\checksums.txt name=checksums.txt
      • published                                    url=https://github.com/umemak/asin2md/releases/tag/v0.1.1
      • took: 11s
  • took: 11s
  • storing release metadata
    • writing                                        file=dist\artifacts.json
    • writing                                        file=dist\metadata.json
  • announcing
  • release succeeded after 22s
```
できた

[Release v0.1.1 · umemak/asin2md](https://github.com/umemak/asin2md/releases/tag/v0.1.1)
