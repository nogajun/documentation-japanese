# APIの紹介
<!-- position: 1 -->

Bludit API(Application Programming Interface)プラグインは、他のシステムとBluditを簡単に統合できるように設計されています。このプラグインを使うと、簡単なHTTPリクエストでデータベースからデータの取得や更新ができます。

<h2 id="installation">インストール</h2>
BluditにはAPIプラグインがプリインストールされているので、プラグインセクションから有効化するだけです。

```bash
管理パネル > ブラグイン > API > 有効化
```

<h2 id="url">URL</h2>
APIのURLは次のとおりです。

```bash
{protocol}://{domain}/api/{endpoint}
````

例

```bash
https://www.example.com/api/pages
```

<h2 id="endpoints">エンドポイントとメソッド</h2>

| エンドポイント | メソッド | 説明 |
|----------|--------|-------------|
| /pages | `GET` | ページのリストを返す |
| /pages/{page key} | `GET` | ページキーでページを返す |
| /pages | `POST` | 新規ページの作成 |
| /pages/{page key} | `PUT` | ページの編集 |
| /pages/{page key} | `DELETE` | ページの削除 |
| /settings | `GET` | Bluditの設定を返す |
| /settings | `PUT` | Bluditの設定の編集 |
| /images | `POST` | 画像をアップロードして、ページのサムネイルを生成 |
| /tags | `GET` | タグとタグに関連するページキーのリストを返す |
| /tags/{tag key} | `GET` | タグキーでタグを返す |
| /categories | `GET` | カテゴリーとカテゴリーに関連するページキーのリストを返す |
| /categories/{category key} | `GET` | カテゴリキーでカテゴリを返す |
| /users | `GET` | システムに登録されているユーザーの一覧を返す |
| /users/{username} | `GET` | プロファイルのユーザーを返す |
| /files/{page key} | `GET` | ページに関連するファイルを返す |

<h2 id="http-response">HTTPレスポンス</h2>

レスポンスのコンテンツ形式は`Content-Type:application/json`です。

本文のデフォルト値です。

| キー | type | 説明 |
|-----|------|-------------|
| status | string | 成功した場合は0を返す。 |
| message | string | 実行に関する簡単なメッセージを返す。 |
| data | array | エンドポイントに対する応答内容 |

<h2 id="http-status-code">HTTPステータスコード</h2>

| HTTPコード | 説明 |
|-----------|-------------|
| 200 | 応答に成功しました。 |
| 400 | 要求が正しくありません。入力がありません。 |
| 401 | APIトークンまたは認証トークンがないか、または間違っています。 |