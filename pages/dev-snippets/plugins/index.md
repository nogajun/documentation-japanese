# プラグイン
<!-- position: 10 -->

プラグインの操作に役立つスニペットです。

## プラグインの有効化

```
<?php
	// Class name of the plugin
	$className = 'pluginAbout';

	activatePlugin($className);
?>
```

## プラグインを無効化

```
<?php
	// Class name of the plugin
	$className = 'pluginAbout';

	deactivatePlugin($className);
?>
```

## プラグインがアクティブ(有効化されている)か確認

```
<?php
	// Class name of the plugin
	$className = 'pluginAbout';

	if (pluginActivated($className)) {
		echo 'The plugin About is activated';
	} else {
		echo 'The plugin About is deactivated';
	}
?>
```

## プラグインを取得
この関数は[Plugin-Object](https://github.com/bludit/bludit/blob/master/bl-kernel/abstract/plugin.class.php)を返します。

プラグインを有効にする必要があります。有効にしないと`getPlugin()`関数は`false`を返します。

```
<?php
	// Class name of the plugin
	$className = 'pluginAbout';

	// Get the Plugin-Object
	$plugin = getPlugin($className);

	// Print the plugin label
	echo $plugin->label();

	// Execute the hook siteSidebar of the plugin and print it
	echo $plugin->siteSidebar();
?>
```
