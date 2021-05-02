# 作成例: 2つ目のテーマ
<!-- position: 101 -->

ここでは2つ目の例として、CSS、Javascript、プラグインの対応などBluditのテーマを最初から作る方法を紹介します。

このテーマは`Mars`と呼びましょう。

もし、このチュートリアルに興味がない場合は、こちらからソースコードをダウンロードできます。 <a href="https://github.com/bludit/examples/tree/master/themes/mars">Mars theme</a>.

<h2 id="folder-structure">フォルダー構造</h2>
`/bl-themes/`フォルダーにテーマのフォルダーを作成します。パスは`/bl-themes/mars/`のようになります。

次に言語、CSS、JSフォルダを作成します。
- `/bl-themes/mars/`フォルダーに`languages`フォルダーを作成します。
- `/bl-themes/mars/`フォルダーに`css`フォルダーを作成します。
- `/bl-themes/mars/`フォルダーに`js`フォルダーを作成します。

```
/bl-themes/mars/
	css/
	js/
	language/
```

<h2 id="name-and-information">名前と情報</h2>
テーマ情報を含むファイルを作成します。このファイルはテーマのルートフォルダーにあり、`metadata.json`という名前にする必要があります。以下のJSONコードを含めてください。

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

`en.json`というテーマの名前と説明を書いたファイルも作成します。下のJSONコードを記述して`/bl-themes/mars/languages/`フォルダーに配置します。

```
{
	"theme-data":
	{
		"name": "Mars",
		"description": "これは2番目のBluditテーマです。"
	}
}
```
<h2 id="index">Index.php</h2>
それでは`index.php`の作業をしましょう。`/bl-themes/mars/`フォルダーに下のHTMLコードを記述したファイルを作成します。

```
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
</head>
<body>

</body>
</html>
```

<h2 id="css-files">CSSファイル</h2>
CSSファイルを追加します。CSSファイルの追加には2つ方法があります。
- `Theme::css()`ヘルパーオブジェクトを使用する
- またはHTMLタグを使う<link href="..." rel="stylesheet" type="text/css" />`

今回は、ヘルパーを使ってCSSファイル`/bl-themes/mars/css/style.css`を追加します。ヘルパーを使用すれば、絶対パスを指定する必要はありません。

```
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">

	<!-- CSS -->
	<?php echo Theme::css('css/style.css') ?>
</head>
<body>

</body>
</html>
```

<h2 id="javascript-files">Javascriptファイル</h2>
JavaScriptファイルを追加します。JavaScriptファイルの追加には2つ方法があります。
- `Theme::js()`ヘルパーオブジェクトを使用する
- またはHTMLタグを使う<script>...</script>`

ここでは、ヘルパーを使ってJavascriptファイル`/bl-themes/mars/js/mars.js`を追加します。ヘルパーを使用すれば、絶対パスを指定する必要はありません。

```
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">

	<!-- CSS -->
	<?php echo Theme::css('css/style.css') ?>

	<!-- Javascript -->
	<?php echo Theme::js('js/mars.js') ?>
</head>
<body>

</body>
</html>
```

<h2 id="plugin-support">プラグインサポートの追加</h2>
プラグインのサポートを追加するには、`Theme::plugins()`ヘルパーを使用します。

サイトのプラグインフックは以下のとおりです。
- `siteHead`にはすべてのプラグインが含まれており、`<head>...</head>`タグ内のコードを返します。
- `siteBodyBegin`にはすべてのプラグインが含まれており、上部の`<body>...</body>`タグ内のコードを返します。ウェルカムバナーやページ上部にあるツールバーに利用できます。
- `siteBodyEnd`にはすべてのプラグインが含まれており、下部の`<body>.</body>`タグ内のコード(JavaScriptコードなど)を返します。

```
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">

	<!-- CSS -->
	<?php echo Theme::css('css/style.css') ?>

	<!-- Javascript -->
	<?php echo Theme::js('js/mars.js') ?>

	<!-- siteHeadフックでプラグインをロード -->
	<?php Theme::plugins('siteHead') ?>
</head>
<body>
	<!-- siteBodyBeginフックでプラグインをロード -->
	<?php Theme::plugins('siteBodyBegin') ?>

	<!-- ここに残りすべてのHTMLコード -->

	<!-- siteBodyBeginフックでプラグインをロード -->
	<?php Theme::plugins('siteBodyEnd') ?>
</body>
</html>
```

<h2 id="site-logo-title-and-slogan">サイトロゴ、タイトル、スローガン</h2>
Site-Objectを使ってロゴやタイトル、スローガンを取得できます。

```
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">

	<!-- CSS -->
	<?php echo Theme::css('css/style.css') ?>

	<!-- Javascript -->
	<?php echo Theme::js('js/mars.js') ?>

	<!-- siteHeadフックからプラグインをロード -->
	<?php Theme::plugins('siteHead') ?>
</head>
<body>
	<!-- siteBodyBeginフックからプラグインをロード -->
	<?php Theme::plugins('siteBodyBegin') ?>

	<img src="<?php echo $site->logo() ?>" alt="" width="128">
	<h1><?php echo $site->title() ?></h1>
	<h2><?php echo $site->slogan() ?></h2>

	<!-- siteBodyBeginフックからプラグインをロード -->
	<?php Theme::plugins('siteBodyEnd') ?>
</body>
</html>
```

<h2 id="where-am-i">私はどこ</h2>
では、サイトのコンテンツを操作してみましょう。

ユーザーがサイトのどのページを参照しているかを特定するには変数`$WHERE_AM_I`を使用します。たとえば、ユーザーがページを閲覧している場合、変数の値は`page`という文字列を持ち、ユーザーがフロントページ(ホームページ)を閲覧している場合は、変数の値は`home`になります。

```
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">

	<!-- CSS -->
	<?php echo Theme::css('css/style.css') ?>

	<!-- Javascript -->
	<?php echo Theme::js('js/mars.js') ?>

	<!-- siteHeadフックからプラグインをロード  -->
	<?php Theme::plugins('siteHead') ?>
</head>
<body>
	<!-- siteBodyBeginフックからプラグインをロード  -->
	<?php Theme::plugins('siteBodyBegin') ?>

	<h1><?php echo $site->title() ?></h1>
	<h2><?php echo $site->slogan() ?></h2>

	<?php if ($WHERE_AM_I=='page'): ?>
		<p>ユーザーは特定のページを見ています</p>
	<?php elseif ($WHERE_AM_I=='home'): ?>
		<p>ユーザーはホームページを見ています</p>
	<?php endif ?>

	<!-- siteBodyBeginフックからプラグインをロード -->
	<?php Theme::plugins('siteBodyEnd') ?>
</body>
</html>
```

<h2 id="main-content">メインコンテンツ</h2>
ユーザーがホームページにいる場合、Bluditはすべての公開ページを含むグローバル配列`$pages`を生成します。各ページは `Page Object` です。

```
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">

	<!-- CSS -->
	<?php echo Theme::css('css/style.css') ?>

	<!-- Javascript -->
	<?php echo Theme::js('js/mars.js') ?>

	<!-- siteHeadフックからプラグインをロード  -->
	<?php Theme::plugins('siteHead') ?>
</head>
<body>
	<!-- siteBodyBeginフックからプラグインをロード  -->
	<?php Theme::plugins('siteBodyBegin') ?>

	<h1><?php echo $site->title() ?></h1>
	<h2><?php echo $site->slogan() ?></h2>

	<?php if ($WHERE_AM_I=='page'): ?>
		<p>ユーザーは特定のページを見ています</p>
	<?php elseif ($WHERE_AM_I=='home'): ?>
		<?php foreach ($content as $page): ?>
			<h3><?php echo $page->title(); ?></h3>
		<?php endforeach ?>
	<?php endif ?>

	<!-- siteBodyBeginフックからプラグインをロード  -->
	<?php Theme::plugins('siteBodyEnd') ?>
</body>
</html>
```

ユーザーが特定のページを表示している場合、BluditはグローバルPage-Object`$page`を生成します。この例では、タイトルとコンテンツを表示します。

```
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">

	<!-- CSS -->
	<?php echo Theme::css('css/style.css') ?>

	<!-- Javascript -->
	<?php echo Theme::js('js/mars.js') ?>

	<!-- siteHeadフックからプラグインをロード  -->
	<?php Theme::plugins('siteHead') ?>
</head>
<body>
	<!-- siteBodyBeginフックからプラグインをロード  -->
	<?php Theme::plugins('siteBodyBegin') ?>

	<h1><?php echo $site->title() ?></h1>
	<h2><?php echo $site->slogan() ?></h2>

	<?php if ($WHERE_AM_I=='page'): ?>
		<h3><?php echo $page->title(); ?></h3>
	<?php elseif ($WHERE_AM_I=='home'): ?>
		<?php foreach ($pages as $page): ?>
			<h3><?php echo $page->title(); ?></h3>
		<?php endforeach ?>
	<?php endif ?>

	<!-- siteBodyBeginフックからプラグインをロード  -->
	<?php Theme::plugins('siteBodyEnd') ?>
</body>
</html>
```

<div class="note">
<div class="title">ダウンロード</div>
<a href="https://github.com/bludit/examples/tree/master/themes/mars">Marsテーマ</a>のソースコードをダウンロード。
</div>
