# プラグインを含める
<!-- position: 6 -->

Bluditはプラグインをサポートしており、各プラグインにはフックがあります。フックは関数で、これらの関数はテーマ内の異なる場所で実行されます。

フックのリストはこちらです。
- https://docs.bludit.com/en/plugins/hooks-list

例としては、フック`siteHead`で有効化されたすべてのプラグインを実行するには、`Theme::plugins()`ヘルパーを使用します。
```
<?php
	Theme::plugins('siteHead');
?>
```

<h2 id="example">設定例</h2>

ここでは、3種類のフックを使用してテーマの正しい場所で実行する方法の例を示します。

```
<!DOCTYPE html>
<html>
	<head>
		<title>Hello</title>

		<?php
			Theme::plugins('siteHead');
		?>
	</head>
<body>

<?php
	Theme::plugins('siteBodyBegin');
?>

<h1>これは見出しです</h1>
<p>これは段落です。</p>

<?php
	Theme::plugins('siteBodyEnd');
?>

</body>
</html>
```
