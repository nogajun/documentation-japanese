# タグ
<!-- position: 6 -->

タグを操作するためのコードスニペット。

タグの定義済み変数
- `$tags`はタグオブジェクトです。[こちらにはクラスがあります](https://github.com/bludit/bludit/blob/master/bl-kernel/tags.class.php)。

<div class="note">
デフォルトでは、タグのデータベースは英数字でソートされます。
</div>

<h2 id="list-all-tags">すべてのタグ一覧を表示</h2>

```
<?php
	// Returns an array with all the tags
	$items = getTags();

	foreach ($items as $tag) {
		// Each tag is an Tag-Object
		echo 'Tag name: '		. $tag->name();
		echo 'Tag key: ' 		. $tag->key();
		echo 'Tag link: ' 		. $tag->permalink();
		echo 'Tag number of pages: ' 	. count($tag->pages());
	}
?>
```

代わりの方法

```
<?php
	foreach ($tags->keys() as $key) {
		// Create Tag-Object
		$tag = new Tag($key);

		echo 'Tag name: '		. $tag->name();
		echo 'Tag key: ' 		. $tag->key();
		echo 'Tag link: ' 		. $tag->permalink();
		echo 'Tag number of pages: ' 	. count($tag->pages());
	}
?>
```

<h2 id="list-tags-that-have-pages">ページを持つタグ一覧</h2>

```
<?php
	$items = getTags();

	foreach ($items as $tag) {
		// Each tag is an Tag-Object
		if (count($tag->pages())>0) {
			echo 'Tag name: '	. $tag->name();
			echo 'Tag key: ' 	. $tag->key();
			echo 'Tag link: ' 	. $tag->permalink();
		}
	}
?>
```

<h2 id="list-all-tags-and-pages">すべてのタグと、そのタグに関連するページ一覧を表示</h2>

```
<?php
	$items = getTags();

	foreach ($items as $tag) {
		// Each tag is an Tag-Object
		echo 'Tag name: ' . $tag->name();

		// The method $tag->pages() returns all the pages keys releated to the tag
		foreach ($tag->pages() as $pageKey) {
			$page = new Page($pageKey);
			echo '- Page title: ' . $page->title();
		}
	}
?>
```

<h2 id="list-all-pages-related-to-a-particular-tag">特定のタグに関連するすべてのページを表示</h2>

```
<?php
        // タグキー
        $tagKey = 'example';

	// タグはTag-Objectです
        $tag = getTag($tagKey);

        // タグ名を出力
        echo 'Tag name: ' . $tag->name();

        // exampleタグ に関連するページタイトルを表示
        foreach ($tag->pages() as $pageKey) {
		$page = new Page($pageKey);
		echo $page->title();
        }
?>
```

<h2 id="get-the-active-tag">アクティブタグの取得</h2>

```
<?php
	// Check if the user is browsing a tag
	if ($WHERE_AM_I=='tag') {
		// Get the tag key from the URL
		$tagKey = $url->slug();

		// Create the Tag-Object
		$tag = new Tag($tagKey);

		// Print the tag name
		echo $tag->name();
	}
?>
```

<h2 id="print-the-tags-of-a-page">ページのタグ</h2>

ページのタグを表示する
```
<?php
	$returnsArray = true;

	$items = $page->tags($returnsArray);

	foreach ($items as $tagKey=>$tagName) {
		echo $tagName;
	}
?>
```

タグとパーマリンクを表示
```
<?php
	$returnsArray = true;

	$items = $page->tags($returnsArray);

	foreach ($items as $tagKey=>$tagName) {
		$tag = new Tag($tagKey);

		echo '<a href="'.$tag->permalink().'">'.$tag->name().'</a>';
	}
?>
```

