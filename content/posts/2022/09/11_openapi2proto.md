---
title: "OpenAPIからgRPCへの移行"
date: "2022-09-11"
tags: ["go", "gRPC"]

---

今あるOpenAPI用の定義yamlファイルからgRPC用のprotoファイルが生成できないかなと思い、検索したら良さそうなものが見つかった。

- [nytimes/openapi2proto: A tool for generating Protobuf v3 schemas and gRPC service definitions from OpenAPI specifications](https://github.com/nytimes/openapi2proto)


https://github.com/umemak/eventsite_go/blob/main/openapi.yml でやってみた。

```sh
$ go install github.com/NYTimes/openapi2proto/cmd/openapi2proto
$ openapi2proto -spec openapi.yml -annotate
syntax = "proto3";

package eventsite;

import "google/api/annotations.proto";
import "google/protobuf/empty.proto";

service EventsiteService {
    // Get all events.
    rpc GetEvents(google.protobuf.Empty) returns (google.protobuf.Empty) {
        option (google.api.http) = {
            get: "/events"
        };
    }

    // Create event.
    rpc PostEvents(google.protobuf.Empty) returns (google.protobuf.Empty) {
        option (google.api.http) = {
            post: "/events"
        };
    }
}
```

serviceは作られているけど、messageは作ってくれてないっぽい。

protoからOpenAPI作るのは比較的多いけど、その逆はほとんどない。
ということは、両方使いたければマスターはprotoで管理したほうが良いのかもしれない。