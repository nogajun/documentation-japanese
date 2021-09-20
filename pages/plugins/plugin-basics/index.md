# プラグインの基本
<!-- position: 1 -->

Bluditのプラグインは`bl-plugins`フォルダにあり、定義された構造を持っています。各プラグインはBluditのオブジェクトで、それぞれ異なるフック(メソッド)を持っています。

<h2 id="structure">フォルダーとファイル構造</h2>
プラグインに必要なフォルダ構造とファイルは次のとおりです。

```
/bl-plugins/{プラグイン名}/
	languages/en.json
	metadata.json
	plugin.php
```

<h2 id="name-and-description">名前と説明</h2>
プラグインの名前と説明は、JSONファイル`languages/en.json`にあります。

```
{
	"plugin-data":
	{
		"name": "Hello World",
		"description": "Print Hello World in the sidebar"
	}
}
```

<h2 id="information">テーマ情報</h2>
プラグインのメタ情報は、JSONファイル`metadata.json`にあります。

```
{
	"author": "Bludit",
	"email": "",
	"website": "https://plugins.bludit.com",
	"version": "1.0",
	"releaseDate": "2020-06-01",
	"license": "MIT",
	"compatible": "3.0",
	"notes": ""
}
```

<h2 id="hello-world">Hello Worldプラグイン</h2>
BluditのHello Worldプラグインです。以下のコードは、`plugin.php`ファイルに記述する必要があります。

```
<?php
	class pluginHello extends Plugin {
		public function siteSidebar() {
			echo 'Hello world';
		}
	}
?>
```

<div class="note">
<div class="title">ダウンロード</div>
<a href="https://github.com/bludit/examples/tree/master/plugins/hello-world">Hello World</a>のソースコードをダウンロード。
</div>
