# フレームワークを含める
<!-- position: 7 -->

Bluditのテーマは非常に柔軟で、フレームワーク(Bootstrap、Foundation、Bulma、UIkit、Semantic UIなど)、Javascriptコードなどを自由に使えます。

このドキュメントでは、いくつかのフレームワークを紹介していますが、ページを編集して自由に追加できます。

<h2 id="jquery">jQueryを含める</h2>

Bluditではパッケージに最新のjQueryが含まれているので、これをヘルパーとして利用できます。
```
<?php
	echo Theme::jquery();
?>
```

HTML出力
```
<script src="https://www.example.com/bl-kernel/js/jquery.min.js"></script>
```

<h2 id="bootstrap">Bootstrapを含める</h2>

Bluditではパッケージに最新のBootstrapが含まれているので、これをヘルパーとして利用できます。

Bootstrap用のJavaScriptファイルを含める
```
<?php
	echo Theme::jsBootstrap();
?>
```

HTML出力
```
<script src="https://www.example.com/bl-kernel/js/bootstrap.bundle.min.js"></script>
```

Bootstrap用CSSファイルを含める
```
<?php
	echo Theme::cssBootstrap();
?>
```

HTML出力
```
<link rel="stylesheet" type="text/css" href="https://www.example.com/bl-kernel/css/bootstrap.min.css">
```

<h2 id="uikit">UIkitを含める</h2>

このフレームワークはBluditのパッケージには含まれていませんが、ヘルパーの`Theme::css()`と`Theme::js()`を使って簡単にインクルードできます。また、UIkit CDNを使うか、ファイルをダウンロードしてテーマにインクルードもできます。

次の例では、CDNからUIkitをインクルードしていますが、行末の`false`に注目してください。これは、外部でホストされたファイルを使用することを関数に伝えるものです。
```
<?php
	echo Theme::css('https://cdnjs.cloudflare.com/ajax/libs/uikit/3.0.0-rc.26/css/uikit.min.css', false);

	echo Theme::js('https://cdnjs.cloudflare.com/ajax/libs/uikit/3.0.0-rc.26/js/uikit.min.js', false);
	echo Theme::js('https://cdnjs.cloudflare.com/ajax/libs/uikit/3.0.0-rc.26/js/uikit-icons.min.js', false);
?>
```

HTML出力
```
<link rel="stylesheet" type="text/css" href="https://cdnjs.cloudflare.com/ajax/libs/uikit/3.0.0-rc.26/css/uikit.min.css">

<script src="https://cdnjs.cloudflare.com/ajax/libs/uikit/3.0.0-rc.26/js/uikit.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/uikit/3.0.0-rc.26/js/uikit-icons.min.js"></script>
```
