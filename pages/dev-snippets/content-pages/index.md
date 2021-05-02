# コンテンツ: ページ
<!-- position: 3 -->

以下の例は、**ページ**コンテンツタイプのものです。これらの例が機能するためには、ページが公開されている(ユーザーに見える)必要があります。

<h2 id="list-all-pages-from-the-active-page">アクティブページのすべてのサブページ一覧を表示</h2>

Bludit には、ユーザーが表示している現在のページのすべてのサブページ (または子ページ) を含む定義済みの`$content`配列があります。この配列は、テーマに使用されます。次のコードは、ページのタイトルとコンテンツを表示します。

```
<?php
	foreach ($content as $page) {
		echo $page->title();
		echo $page->content();
	}
?>
```

<h2 id="list-the-latest-5-pages">最新5ページを表示</h2>

このコードスニペットは、ステータスが`公開済み`の最新5ページの`タイトル`を表示します。

```
<?php
	// Page number, the first page is 1
	$pageNumber = 1;

	// Number of items to return
	$numberOfItems = 5;

	// Only get the pages with the status published
	$onlyPublished = true;

	// Get the list of keys of pages
	$items = $pages->getList($pageNumber, $numberOfItems, $onlyPublished);

	foreach ($items as $key) {
		// buildPage function returns a Page-Object
		$page = buildPage($key);

		// Print the page title
		echo $page->title();
	}
?>
```

<h2 id="list-all-pages">すべてのページ一覧を表示</h2>

このコードスニペットは、ステータスが`公開済み`のシステム内すべてのページの`タイトル`を表示します。ページ数によっては、パフォーマンスに影響を与えることがあるのでご注意ください。

```
<?php
	// Page number of the paginator, the first page is 1
	$pageNumber = 1;

	// The value -1 tell to Bludit to returns all the pages on the system
	$numberOfItems = -1;

	// Only get the pages with the satus published
	$onlyPublished = true;

	// Get the list of keys of pages
	$items = $pages->getList($pageNumber, $numberOfItems, $onlyPublished);

	foreach ($items as $key) {
		// buildPage function returns a Page-Object
		$page = buildPage($key);

		// Print the page title
		echo $page->title();
	}
?>
```

## サブページの操作
Bluditは1レベルのサブページをサポートしています。

サブページを正しく処理するには、`位置`で順序フィルタを設定する必要があります。
