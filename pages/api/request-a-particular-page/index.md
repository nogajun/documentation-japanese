# 特定のページをリクエスト
<!-- position: 3 -->

ページキーで特定のページを取得します。

APIへのすべてのリクエストには、`APIトークン`が必要です。トークンは、APIプラグインの設定で確認できます。

```bash
管理者パネル > ブラグイン > API > APIトークン
```

<h2 id="request">HTTPリクエスト</h2>

```bash
GET /api/pages/{page key}
```

<h2 id="parameters">パラメータ</h2>

| キー | 値 | デフォルト値 |
|-----|-------|---------------|
| `required` token | `string` APIトークン | |

<h2 id="response">レスポンス</h2>

```bash
HTTP Code: 200
Content-Type: application/json
Body:
{
	"status": "0",
	"message": "Page filtered by key: my-dog",
	"data": {
		"key": "my-dog",
		"title": "My dog",
		"content": "...",
		"contentRaw": "...",
		"description": "...",
		"type": "published",
		"slug": "my-dog",
		"date": "2019-02-02 00:09:38",
		"dateUTC": "2019-02-02 22:09:38",
		"tags": "",
		"permalink": "https://www.example.com/my-dog",
		"coverImage": false,
		"coverImageFilename": false
	}
}
```

<h2 id="curl-example">CURLコマンド例</h2>
You can request a particular page by the page key.

The following example shows how to get the page with the key `my-dog`.

```bash
$ curl -X GET "https://www.example.com/api/pages/my-dog?token=80a09ba055b73f68e3c9e7c9ea12b432"
```

レスポンス本体

```bash
{
	"status": "0",
	"message": "Page filtered by key: my-dog",
	"data": {
		"key": "my-dog",
		"title": "My dog",
		"content": "...",
		"contentRaw": "...",
		"description": "...",
		"type": "published",
		"slug": "my-dog",
		"date": "2019-02-02 00:09:38",
		"dateUTC": "2019-02-02 22:09:38",
		"tags": "",
		"permalink": "https://www.example.com/my-dog",
		"coverImage": false,
		"coverImageFilename": false
	}
}
```

<h2 id="javascript-example">Javascriptの例</h2>
You can use the [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) to get the page.

```bash
<script>
	fetch("https://www.example.com/api/pages/my-dog?token=eaf5df0a626145cc6d37b76f3eccc826", {
		method: 'get'
	}).then(function(response) {
		return response.json();
	}).then(function(json) {
		console.log(json.data);
	});
</script>
```
