# ページの編集
<!-- position: 5 -->

ページを編集します。

APIへのすべてのリクエストには、`APIトークン`が必要です。トークンは、APIプラグインの設定で確認できます。

```bash
管理パネル > ブラグイン > API > APIトークン
```

コンテンツを書き込むためのAPIへのすべてのリクエストは、`認証トークン`を提供する必要があります。このトークンを取得するには、`管理者`ロールを持つユーザーが必要です。ユーザープロファイルから`認証トークン`を取得します。

```bash
管理パネル > 管理 > ユーザー > {ユーザー名} > セキュリティ > 認証トークン
```

<h2 id="request">HTTPリクエスト</h2>

```bash
PUT /api/pages/{key}
```

<h2 id="parameters">パラメータ</h2>

| キー | 値 | デフォルト値 |
|-----|-------|---------------|
| `required` token | `string` APIトークン | |
| `required` authentication | `string` 認証トークン | |
| title | `string` ページタイトル | |
| content | `string` ページ内容 | |
| tags | `string` ページタグ | |
| type | `string` ページタイプ | |
| date | `string` ページ日付 | |
| dateModified | `string` ページ修正日 | |
| position | `string` ページ位置 | |
| coverImage | `string` ページカバー画像 | |
| category | `string` ページカテゴリー | |
| template | `string` ページテンプレート | |
| noindex | `string` noindexページ | |
| nofollow | `string` nofollowページ | |
| noarchive | `string` noarchiveページ | |

<h2 id="response">レスポンス</h2>

```bash
HTTP Code: 200
Content-Type: application/json
Body:
{
	"status": "0",
	"message": "Page edited.",
	"data": {
		"key": "<page key>"
	}
}
```

<h2 id="curl-example">CURLコマンド例</h2>
以下のcurlの例は、キー`my-dog`を持つページを編集する例です。

ファイル`data.json`の内容

```bash
{
	"token": "24a8857ed78a8c89a91c99afd503afa7",
	"authentication": "193569a9d341624e967486efb3d36d75",
	"title": "My dog",
	"content": "Content of the page here, support Markdown code and HTML code."
}
```

コマンドを実行し、`data.json`ファイルを添付します。

```bash
$ curl  -X PUT \
	-H "Content-Type: application/json" \
	-d @data.json \
	"https://www.example.com/api/pages/my-dog"
```

レスポンス本体

```bash
{
	"status": "0",
	"message": "Page edited.",
	"data": {
		"key": "my-dog"
	}
}
```
