# プラグイン用のカスタムフック
<!-- position: 4 -->

Bluditはプラグインのカスタムフックをサポートしています。独自のフックを作成してどこからでも呼び出せます。

<div class="note">
この機能はBludit v3.13から実装されています。
</div>

## 設定例
次の例では、2つのカスタムフック`select`と`insert`を作成しています。

これを動作させるには、配列`$this->customHooks`内のフック(オブジェクトメソッド)をメソッド`init()`内に追加することを忘れないでください。

```php
<?php

class MyHooks extends Plugin {

	public function init()
	{
        $this->customHooks = array(
            'select',
            'insert'
        );
	}

	public function select()
	{
		echo 'Custom hook select';
	}

	public function insert()
	{
		echo 'Custom hook insert';
	}
}

?>
```

プラグインを有効化したあとは、テーマで行う場合と同じようにヘルパー`Theme::plugins`を介してカスタムフックを呼び出せます。

```php
<?php
	...
	Theme::plugins('select');
	...
	Theme::plugins('insert');
?>
```
