# テーマの翻訳
<!-- position: 2 -->

各テーマには`languages`フォルダーがあります。このフォルダーには、言語ごとに異なる言語ファイルを作成できます。

```
/bl-themes/{テーマ名}/languages/
	de_DE.json
	en.json
	es.json
	fr_FR.json
	...
```

<div class="note">
<div class="title">ファイルエンコーディング</div>
すべての辞書ファイルは<b>JSON</b>ファイルで、<b>UTF-8</b>でエンコーディングされています。
</div>

これは英語の言語ファイル(`en.json`)の例です。`en.json`ファイルの各行はキーと値のペアで、左側がキー、右側が値になっています。

```
{
	"theme-data":
	{
		"name": "Pure",
		"description": "Simple and clean, based on the framework Pure.css."
	}
}
```

`theme-data`というフィールドがあります。このフィールドには、テーマの名前と説明があります。

これはスペイン語言語ファイルの例です。このファイルは`/bl-themes/{テーマ名}/languages/es.json`にあります。

```
{
	"theme-data":
	{
		"name": "Pure",
		"description": "Simple y minimalista, basado en el framework Pure.css."
	}
}
```
