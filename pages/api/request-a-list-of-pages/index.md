# ページリストのリクエスト
<!-- position: 2 -->

ページのリストを取得します。

APIへのすべてのリクエストには、`APIトークン`が必要です。トークンは、APIプラグインの設定で確認できます。

```bash
管理者パネル > ブラグイン > API > APIトークン
```

<h2 id="request">HTTPリクエスト</h2>

```bash
GET /api/pages
```

<h2 id="parameters">パラメータ</h2>

| キー | 値 | デフォルト値 |
|-----|-------|---------------|
| `required` token | `string` APIトークン | |
| published | `boolean` 公開されたページを返す。 | `true` |
| sticky | `boolean` 固定ページを返す。 | `false` |
| static | `boolean` 静的ページを返す。 | `false` |
| draft | `boolean` 下書きページを返す | `false` |
| untagged | `boolean` タグのないページを返す。 | `false` |

<h2 id="response">レスポンス</h2>

```bash
HTTP Code: 200
Content-Type: application/json
Body:
{
	"status": "0",
	"message": "List of pages, amount of items: 15",
	"data": [
		{
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
		},
		{
			....
		}
	]
}
```

<h2 id="curl-example">CURLコマンド例</h2>
次のリクエストは、APIで制限された公開ページと静的ページのリストを返します。この制限は、APIの設定で変更できます。

```bash
$ curl -X GET "https://www.example.com/api/pages?token=80a09ba055b73f68e3c9e7c9ea12b432&published=true&static=true"
```

レスポンス本体

```bash
{
        "status": "0",
        "message": "List of pages, number of items: 15",
        "data": [
		{
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
                },
                {
                        ....
                }
        ]
}
```

<h2 id="javascript-example">Javascriptの例</h2>
Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)を使って、ページの一覧を取得できます。

```
<script>
	fetch("https://www.example.com/api/pages?token=eaf5df0a626145cc6d37b76f3eccc826&published=true&static=true", {
		method: 'get'
	}).then(function(response) {
		return response.json();
	}).then(function(json) {
		console.log(json.data);
	});
</script>
```
