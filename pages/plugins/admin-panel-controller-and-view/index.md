# プラグインからの管理パネルのコントローラーとビュー
<!-- position: 3 -->

Bluditでは、プラグインから管理パネルのコントローラーとビューを簡単に作成できます。

<div class="note">
この機能はBludit v3.13から実装されています。
</div>

## メモ
- Bluditのデフォルトでは、スタイリングに[Bootstrap](https://getbootstrap.com/)を使用しますが管理ビューでも使用できます。
- 管理ビューのエンドポイントは`/admin/plugin/<プラグイン名>`です。

## 例: Hello world!
次のプラグインは、メタデータ`<title>`を変更し、ビューはシンプルに`Hello world!`と返します。

プラグインを有効にすると、ビュー`https://www.example.com/admin/plugin/hello`に移動できます。

```php
<?php

class Hello extends Plugin {

	public function adminController()
	{
		global $layout;
		$layout["title"] = "Hello Plugin | Bludit";
	}

	public function adminView()
	{
		return 'Hello world!';
	}

	public function adminSidebar()
	{
		$pluginName = Text::lowercase(__CLASS__);
		$url = HTML_PATH_ADMIN_ROOT.'plugin/'.$pluginName;
		$html = '<a id="current-version" class="nav-link" href="'.$url.'">Hello world</a>';
		return $html;
	}
}
?>
```

## 例: フォームからの設定変更
次のプラグインは、Bluditの設定を変更する機能があります。ビューにはフォームが表示され、コントローラは`POST`メソッドを管理します。

プラグインを有効にすると、こちら`https://www.example.com/admin/plugin/settings`からビューにアクセスできます。

```php
<?php

class CustomAdmin extends Plugin {

	public function adminController()
	{
		// Check if the form was sent
		if ($_SERVER['REQUEST_METHOD'] == 'POST') {
			global $site;
			$site->set(array('title'=>$_POST['title']));
		}
	}

	public function adminView()
	{
		// Token for send forms in Bludit
		global $security;
		$tokenCSRF = $security->getTokenCSRF();

		// Current site title
		global $site;
		$title = $site->title();

		// HTML code for the form
		$html = '
			<h2>Settings</h2>
			<form method="post">
			<input type="hidden" id="jstokenCSRF" name="tokenCSRF" value="'.$tokenCSRF.'">
			<div class="form-group">
				<label for="title">Site title</label>
				<input type="text" class="form-control" id="title" name="title" value="'.$title.'">
			</div>
			<button type="submit" class="btn btn-primary">Submit</button>
			</form>
		';
		return $html;
	}

	public function adminSidebar()
	{
		$pluginName = Text::lowercase(__CLASS__);
		$url = HTML_PATH_ADMIN_ROOT.'plugin/'.$pluginName;
		$html = '<a id="current-version" class="nav-link" href="'.$url.'">Custom Admin Form</a>';
		return $html;
	}
}
```

完全なプラグインサンプルは、こちらからダウンロードできます。
- https://github.com/bludit/examples/tree/master/plugins/custom-controller-view-admin-panel
