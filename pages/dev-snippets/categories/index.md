# カテゴリー
<!-- position: 5 -->

ここでは、カテゴリーを操作するコードスニペットを紹介します。

カテゴリの定義済み変数
- `$categories`はCategoriesオブジェクトです。[ここにクラスがあります](https://github.com/bludit/bludit/blob/master/bl-kernel/categories.class.php)。

<div class="note">
デフォルトでは、カテゴリーのデータベースはアルファベット順にソートされます。
</div>

<h2 id="list-all-categories">すべてのカテゴリのリスト表示</h2>

```
<?php
	$items = getCategories();

	foreach ($items as $category) {
		// Each category is an Category-Object
		echo 'Category name: '			. $category->name();
		echo 'Category key: ' 			. $category->key();
		echo 'Category description: ' 		. $category->description();
		echo 'Category template: ' 		. $category->template();
		echo 'Category link: ' 			. $category->permalink();
		echo 'Category number of pages: ' 	. count($category->pages());
	}
?>
```

代わりの方法

```
<?php
	foreach ($categories->keys() as $key) {
		// Create Category-Object
		$category = new Category($key);

		echo 'Category name: '			. $category->name();
		echo 'Category key: ' 			. $category->key();
		echo 'Category description: ' 		. $category->description();
		echo 'Category template: ' 		. $category->template();
		echo 'Category link: ' 			. $category->permalink();
		echo 'Category amount of pages: ' 	. count($category->pages());
	}
?>
```

<h2 id="list-categories-that-have-pages">ページのあるカテゴリー一覧を表示</h2>

```
<?php
	$items = getCategories();

	foreach ($items as $category) {
		// Each category is an Category-Object
		if (count($category->pages())>0) {
			echo 'Category name: '	. $category->name();
			echo 'Category key: ' 	. $category->key();
			echo 'Category link: ' 	. $category->permalink();
		}
	}
?>
```

<h2 id="list-all-categories-and-pages">すべてのカテゴリーと各カテゴリーに関連するページ一覧を表示</h2>

```
<?php
	$items = getCategories();

	foreach ($items as $category) {
		// Each category is an Category-Object
		echo 'Category name: ' . $category->name();

		// The method $category->pages() returns all the pages keys releated to the category
		foreach ($category->pages() as $pageKey) {
			$page = new Page($pageKey);
			echo '- Page title: ' . $page->title();
		}
	}
?>
```

<h2 id="list-all-pages-related-to-a-particular-category">特定のカテゴリーに関連するすべてのページ一覧を表示</h2>

```
<?php
        // Category key
        $categoryKey = 'example';

		// The category is an Category-Object
        $category = getCategory($categoryKey);

        // Print the category name
        echo 'Category name: ' . $category->name();

        // Print the pages title related to the category "example"
        foreach ($category->pages() as $pageKey) {
			$page = new Page($pageKey);
			echo $page->title();
        }
?>
```

<h2 id="get-the-active-category">アクティブなカテゴリーを取得</h2>

```
<?php
	// Check if the user is browsing a category
	if ($WHERE_AM_I=='category') {
		// Get the category key from the URL
		$categoryKey = $url->slug();

		// Create the Category-Object
		$category = new Category($categoryKey);

		// Print the category name
		echo $category->name();

		// Print the category description
		echo $category->description();
	}
?>
```
