# 作成例: はじめてのテーマ
<!-- position: 101 -->

新しく`Coffee`と名付けたシンプルなテーマを作成しましょう。

- `/bl-themes/`フォルダーにテーマを作成します。パスは`/bl-themes/coffee/`です。
- `/bl-themes/coffee/`フォルダーに`languages`フォルダーを作成します。
- `/bl-themes/coffee/languages/`>フォルダーに`en.json`ファイルを作成します。
-  `/bl-themes/coffee/`フォルダーに`metadata.json`ファイルを作成します。
-  `/bl-themes/coffee/`フォルダーに`index.php`ファイルを作成します。

作成すると、以下のようなフォルダ/ファイル構成になっているはずです。

```
/bl-themes/coffee/
	languages/en.json
	metadata.json
	index.php
```

次にファイルの内容を作りましょう。まず、`index.php`に以下のHTMLとPHPのコードを追加してみましょう。

```
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title>Bludit</title>
</head>
<body>
	<?php foreach ($content as $page): ?>

		<h1><?php echo $page->title(); ?></h1>
		<div><?php echo $page->content(); ?></div>
		<hr>

	<?php endforeach; ?>
</body>
</html>
```

`languages/en.json`ファイルを編集して、テーマの名前と説明を追加します。

```
{
	"theme-data":
	{
		"name": "Coffee",
		"description": "これは初めてのBluditテーマです。"
	}
}
```

ここで、`metadata.json`ファイルを編集して、テーマについての情報を完成させます。

```
{
	"author": "Bludit",
	"email": "",
	"website": "",
	"version": "1.0",
	"releaseDate": "2019-01-01",
	"license": "MIT",
	"compatible": "3.0",
	"notes": ""
}
```

おめでとうございます！初めてのBluditテーマができましたね。設定に移動して、テーマを有効にできます。
