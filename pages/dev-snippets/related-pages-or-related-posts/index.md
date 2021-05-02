# 関連ページや関連記事
<!-- position: 10 -->

ページに関連するページ一覧を取得します。Bluditのページと記事は概念としては同じであることを思い出してください。

## 例: 関連ページの取得
次の例は、現在のページから関連する各ページのタイトルを表示します。

```php
<?php
$relatedPages = $page->related();
foreach ($relatedPages as $pageKey) {
	$related = new Page($pageKey);
	echo $related->title();
}
?>
```

## 例: 関連ページのソート
`->related()`メソッドは、ソートをせずにページリストを返します。次の例のように、日付でソートもできます。

```php
<?php
// Insert in array by unixtimestamp
$sort = array();
$relatedPages = $page->related();
foreach ($relatedPages as $pageKey) {
	$tmp = new Page($pageKey);
	$sort[$tmp->date['U']] = new Page($pageKey);
}

// Sort array by key which is unixtimestamp
krsort($sort);

// Print related page title and date
foreach ($sort as $related) {
	echo $related->title();
	echo $related->date();
}
?>
```
