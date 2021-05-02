# Favicon
<!-- position: 5 -->

Bluditでは、開発者がより少ないコードで書けるようにヘルパーを提供しています。

このチュートリアルでは以下の名前を使用します。
- テーマの名前 `box`
- サイトURL `https://www.example.com`
- テーマパス `/bl-themes/box/`
- Faviconファイルパス `/bl-themes/box/favicon.png`

ヘルパー`Theme::`の次のメソッドはfaviconのヘッドタグを生成します。デフォルトで返すMIMEタイプは、`image/png`です。
```
<?php
	echo Theme::favicon('favicon.png');
?>
```

HTML出力
```
<link rel="shortcut icon" href="https://www.example.com/bl-themes/box/favicon.png" type="image/png">
```

また、`.ico`などの別のfaviconタイプを使用する場合は、MIMEタイプを指定できます。
```
<?php
	echo Theme::favicon('favicon.ico', 'image/x-icon');
?>
```

HTML出力
```
<link rel="shortcut icon" href="https://www.example.com/bl-themes/box/favicon.ico" type="image/x-icon">
```

<h2 id="example">設定例</h2>

ここでは、テーマにfaviconを含める例を紹介します。

```
<!DOCTYPE html>
<html>
	<head>
		<title>Hello</title>

		<?php
			echo Theme::favicon('favicon.png');
		?>
	</head>
<body>

<h1>これは見出しです</h1>
<p>これは段落です。</p>

</body>
</html>
```
