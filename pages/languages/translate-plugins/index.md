# プラグインの翻訳
<!-- position: 1 -->

各プラグインには`languages`というフォルダがあり、このフォルダ内に各言語用の言語ファイルを作成します。

```
/bl-plugins/{プラグイン名}/languages/
	de_DE.json
	en.json
	es.json
	fr_FR.json
	...
```

<div class="note">
<div class="title">ファイルエンコーディング</div>
すべての言語ファイルは<b>JSON</b>ファイルで、<b>UTF-8</b>でエンコーディングされています。
</div>

これは英語の言語ファイル(`en.json`)の例です。`en.json`ファイルの各行はキーと値のペアで左側がキー、右側が値になっています。

```
{
	"plugin-data":
	{
		"name": "Page list",
		"description": "Shows the list of pages in order."
	},

	"home": "Home",
	"show-home-link": "Show home link"
}
```

`plugin-data`というフィールドがあります。このフィールドにはプラグインの名前と説明が入ります。次のフィールドには、`home`および`show-home-link`というプラグインのメッセージがあります。

これはスペイン語言語ファイルの例です。このファイルは`/bl-plugins/{プラグイン名}/languages/es.json`にあります。

```
{
	"plugin-data":
	{
		"name": "Listado de paginas",
		"description": "Muestra el listado de paginas en orden."
	},

	"home": "Inicio",
	"show-home-link": "Mostrar link de la pagina de incio"
}
```
