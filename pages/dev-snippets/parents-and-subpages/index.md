# 親ページとサブページ
<!-- position: 7 -->

<div class="note">
以下のスニペットはBludit v2.3以上で動作します。
</div>

## ページに子(サブページ)があるか確認

```
<?php
	// The variable $page is an Page-Object
	if ($page->hasChildren())) {
		echo 'The page has children';
	} else {
		echo 'The page does not have children';
	}
?>
```

## ページすべてのサブページ一覧を表示

```
<?php
	// The variable $page is an Page-Object
	$children = $page->children();

	// Each child is a Page-Object
	foreach ($children as $child) {
		echo $child->title();
	}
?>
```

## ページに子(親がある)かどうかを確認

```
<?php
	// The variable $page is an Page-Object
	if ($page->isChild())) {
		echo 'The page is a child';
	} else {
		echo 'The page is not a child';
	}
?>
```

## 子ページから親ページのタイトルを表示
ページに子ページがある場合は、`parentMethod()`で親ページのメソッドを呼び出せます。

```
<?php
	// The variable $page is an Page-Object
	if ($page->isChild())) {
		echo 'Title of the parent page: ' . $page->parentMethod('title');
	} else {
		echo 'The page is not child';
	}
?>
```

## ナビゲーションバーの表示
親ページには子ページがある場合と無い場合があります。

```
<?php
	// Get the list of parent pages
	$parents = buildParentPages();

	foreach ($parents as $parent) {
		echo $parent->title();

		// Check if the page has children
		if ($parent->hasChildren()) {
			// Get the list of children
			$children = $parent->children();

			foreach ($children as $child) {
				echo " > " . $child->title();
			}
		}
	}
?>
```
