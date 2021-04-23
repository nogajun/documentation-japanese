# CSSファイル
<!-- position: 3 -->

Bluditは、開発者がより少ないコードで書けるようにヘルパーを提供しています。

このチュートリアルでは以下の名前を使用します:
- テーマの名前 `box`
- サイトURL `https://www.example.com`
- テーマパス `/bl-themes/box/`
- CSSファイルパス `/bl-themes/box/style.css`

それでは、`style.css`というCSSファイルを追加しましょう。このファイルは、`/bl-themes/box/style.css`にあります。`Theme::`ヘルパーを使用する場合は、絶対パスを気にする必要はありません。
```
<?php
	echo Theme::css('style.css');
?>
```

HTML出力
```
<link rel="stylesheet" type="text/css" href="https://www.example.com/bl-themes/box/style.css">
```

<h2 id="example">設定例</h2>

次のHTMLとPHPのスニペットは、テーマに2つのCSSファイルを含める方法の例です。

```
<!DOCTYPE html>
<html>
	<head>
		<title>Hello</title>

		<?php
			echo Theme::css('style.css');
			echo Theme::css('buttons.css');
		?>
	</head>
<body>

<h1>これは見出しです</h1>
<p>これは段落です。</p>

</body>
</html>
```
