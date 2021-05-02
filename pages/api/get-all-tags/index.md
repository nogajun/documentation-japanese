# すべてのタグを取得
<!-- position: 7 -->

すべてのタグと各タグに関連するページキーを取得します。

APIへのすべてのリクエストには、`APIトークン`が必要です。

<h2 id="request">リクエスト</h2>

- エンドポイント: `/api/tags`
- メソッド: `GET`

以下は、このエンドポイントで使用できるパラメータ一覧です。

| キー | 値 | デフォルト値 |
|-----|-------|---------------|
| `required` token | `string` APIトークン | |

<h2 id="response">レスポンス</h2>

- HTTPコード: `200`
- コンテンツタイプ: `application/json`

```
{
  "status": "0",
  "message": "List of tags.",
  "data": [
    {
      "name": "Bludit",
      "description": "",
      "template": "",
      "list": [
        "follow-bludit"
      ],
      "key": "bludit"
    },
    {
      "name": "CMS",
      "description": "",
      "template": "",
      "list": [
        "follow-bludit"
      ],
      "key": "cms"
    },
    {
      "name": "Flat files",
      "description": "",
      "template": "",
      "list": [
        "follow-bludit"
      ],
      "key": "flat-files"
    }
  ]
}
```

<h2 id="curl-example">CURLコマンド例</h2>
次のリクエストは、APIで制限された公開ページと静的ページのリストを返します。この制限は、APIの設定で変更できます。

```
$ curl -X GET \
	-G "https://www.example.com/api/tags" \
	-d "token=80a09ba055b73f68e3c9e7c9ea12b432"
```

出力
```
{
  "status": "0",
  "message": "List of tags.",
  "data": [
    {
      "name": "Bludit",
      "description": "",
      "template": "",
      "list": [
        "follow-bludit"
      ],
      "key": "bludit"
    },
    {
      "name": "CMS",
      "description": "",
      "template": "",
      "list": [
        "follow-bludit"
      ],
      "key": "cms"
    },
    {
      "name": "Flat files",
      "description": "",
      "template": "",
      "list": [
        "follow-bludit"
      ],
      "key": "flat-files"
    }
  ]
}
```

<h2 id="javascript-example">Javascriptの例</h2>
[Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)を使ってタグ一覧を取得できます。

```
<script>
	fetch("https://www.example.com/api/tags?token=eaf5df0a626145cc6d37b76f3eccc826", {
		method: 'get'
	}).then(function(response) {
		return response.json();
	}).then(function(json) {
		console.log(json.data);
	});
</script>
```
