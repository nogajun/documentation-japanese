# タイトルと説明
<!-- position: 2 -->

Bluditは、開発者がより少ないコードで、そしてクリーンに保つ手助けをするためのヘルパーを提供しています。

<h2 id="title">タイトル</h2>

動的コンテンツを含む`<title>`ヘッドタグを出力します。タイトルは、サイト設定で定義された設定が使用されます。
```
<?php
	echo Theme::metaTags('title');
?>
```

HTML出力
```
<title>Page title | Title site</title>
```

<h2 id="description">説明</h2>

動的コンテンツを含む`<description>`ヘッドタグを出力します。説明は、サイト設定で定義されている設定が使用されます。
```
<?php
	echo Theme::metaTags('description');
?>
```

HTML出力
```
<meta name="description" content="Description about your site">
```

<h2 id="example">設定例</h2>

ここでは、テーマからTitleとDescriptionを使用する例を紹介します。

```
<!DOCTYPE html>
<html>
	<head>
		<?php
			echo Theme::metaTags('title');
			echo Theme::metaTags('description');
		?>
	</head>
<body>

<h1>これは見出しです</h1>
<p>これは段落です。</p>

</body>
</html>
```
