# Javascriptファイル
<!-- position: 4 -->

Bluditでは、開発者がより少ないコードで書けるようにヘルパーを提供しています。

このチュートリアルでは以下の名前を使用します。
- テーマの名前 `box`
- サイトURL `https://www.example.com`
- テーマパス `/bl-themes/box/`
- Javascriptファイルパス `/bl-themes/box/main.js`

`/bl-themes/box/main.js`に置く、Javascriptファイル`main.js`を追加してみましょう。 `Theme::`ヘルパーを使用する場合は、絶対パスを気にする必要はありません。
```
<?php
	echo Theme::js('main.js');
?>
```

HTML出力
```
<script src="https://www.example.com/bl-themes/box/main.js"></script>
```

<h2 id="example">設定例</h2>

ここでは、テーマに2つのJavaScriptファイルを含める完全な方法を紹介します。

```
<!DOCTYPE html>
<html>
	<head>
		<title>Hello</title>
	</head>
<body>

<h1>これは見出しです</h1>
<p>これは段落です。</p>

<?php
	echo Theme::js('main.js');
	echo Theme::js('buttons.js');
?>

</body>
</html>
```
