# フォルダー構造
<!-- position: 2 -->

Bluditの基本的なフォルダー構造は以下の通りです。

```
/bl-content/	<-- データベースとアップロードされた画像
/bl-kernel/		<-- Bluditコア
/bl-languages/	<-- 言語ファイル
/bl-plugins/	<-- プラグイン
/bl-themes/		<-- テーマ
```

## bl-content

このフォルダーは非常に重要で、Bluditが保存するデータベースや画像といったすべてのファイルが保存される場所です。Bluditを更新する前には、このフォルダーのバックアップを取ることを強く推奨します。

```
/bl-content/

	databases/
		plugins/		<-- データベース: プラグイン
		pages.php		<-- データベース: ページ
		security.php	<-- データベース: ブラックリスト、ブルートフォース保護、その他
		site.php		<-- データベース: サイト変数、名前、説明、スローガン、その他
		tags.php		<-- データベース: タグ
		users.php		<-- データベース: ユーザー

	pages/				<-- コンテンツ: ページ
		about/index.txt
		food/index.txt

	tmp/				<-- テンポラリファイル

	uploads/			<-- アップロードファイル
		profiles/		<-- プロファイル画像
		thumbnails/		<-- サムネイル画像
		photo1.jpg
		photo2.png

	workspaces/			<-- プラグインの作業スペース
```

## bl-kernel

このフォルダーには、Bluditのコア部分が含まれます。

## bl-languages

このフォルダーには、すべての言語ファイルが含まれます。各ファイルは、UTF-8でエンコードされたJSONドキュメントです。

```
/bl-languages/
	bg_BG.json
	cs_CZ.json
	de_CH.json
	en.json
	es.json
	...
```

## bl-plugins

このフォルダーにはすべてのプラグインが含まれます。ダウンロードしたプラグインは、ここにアップロードしてください。

```
/bl-plugins/
	about/
	disqus/
	rss/
	sitemap/
	tinymce/
	...
```

## bl-themes
このフォルダーにはすべてのテーマが含まれます。ダウンロードしたテーマは、ここにアップロードしてください。

```
/bl-themes/
	alternative/
	blogx/
	...
```
