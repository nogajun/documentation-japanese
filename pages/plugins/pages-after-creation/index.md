# ページ: 作成後
<!-- position: 5 -->

ページが作成されると、Bludit はフック`afterPageCreate`を呼び出します。このフックは、スケジューラーで作成されたページに対しても呼び出されます。

<div class="note">
この機能はBludit v3.13から実装されています。
</div>

## 例: タイトルに文字列を追加する
次のプラグインは、ページを作成後、ページの先頭に文字列を追加します。

```php
<?php

class TitleAppender extends Plugin {

	public function afterPageCreate($key)
	{
		$page = new Page($key);
		$currentTitle = $page->title();
		$newTitle = 'Summer: '.$currentTitle;

		global $pages;
		$pages->edit(array(
				'key'=>$key,
				'title'=>$newTitle
		));
	}

}

?>
```

完全なサンプルプラグインは、こちらからダウンロードできます。
- https://github.com/bludit/examples/tree/master/plugins/title-appender
