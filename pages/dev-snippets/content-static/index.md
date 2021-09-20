# コンテンツ: 静的ページ
<!-- position: 4 -->

このセクションでは、[静的ページ](../../content/content-basics#static)のコンテンツ関連を扱っています。

## すべての静的ページを表示
Bluditには、`$staticContent`という[静的ページ用の定義済み変数](../../developers/predefined-variables#staticContent)があります。この変数は、すべての静的ページを含む配列です。

```
<?php
	// Each static page is an Page-Object
	foreach ($staticContent as $page) {
		echo $page->title();
	}
?>
```
