---
title: "React Admin"
date: "2022-09-25"
tags: ["react"]

---

[React Admin - Open-Source Framework for B2B applications](https://marmelab.com/react-admin/)

[react-adminを使って5分で作るハイカラDashboard](https://zenn.dev/engstt/articles/bcdd5c4c3f5b29)を参考に、やってみた。

本当はNext.jsでやりたかったので、[How to Run React-Admin On Next.Js](https://marmelab.com/blog/2022/02/02/bootstrap-your-react-admin-project-with-nextjs.html)も試してみたのだけど、うまくいかなかった。

→公式の[React-admin - My First Project Tutorial](https://marmelab.com/react-admin/NextJs.html)を見ながらやったらできた。

OpenAPIで生成したサーバーだと、`X-Total-Count`ヘッダーがないとエラーになったので、`routers.go`に追加した。
```go
func EncodeJSONResponse(i interface{}, status *int, w http.ResponseWriter) error {
	w.Header().Set("Content-Type", "application/json; charset=UTF-8")
	c := 0
	if r, ok := i.([]Event); ok {
		c = len(r)
	}
	w.Header().Set("X-Total-Count", fmt.Sprint(c))
	w.Header().Set("Access-Control-Expose-Headers", "X-Total-Count")
	if status != nil {
		w.WriteHeader(*status)
	} else {
		w.WriteHeader(http.StatusOK)
	}

	return json.NewEncoder(w).Encode(i)
}
```
このやり方で合っているかは自信ないし、modelが増減するたびにif追加しないといけないのは良くない気がする。

とりあえずは動いたので、ヨシ。
