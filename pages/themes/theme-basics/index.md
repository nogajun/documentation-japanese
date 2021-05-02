# テーマの基礎知識
<!-- position: 1 -->

Bluditのテーマは非常に柔軟で、どんなフレームワーク([Bootstrap](http://getbootstrap.com/), [Foundation](https://foundation.zurb.com/), [Bulma](https://bulma.io), [UIkit](https://getuikit.com/), [Semantic UI](https://semantic-ui.com),など)でも、どんなJavascriptのコードでも自由に利用できます。

すべてのテーマは`bl-themes`フォルダーにあり、あらかじめ定義された構造を持っています。

<h2 id="structure">フォルダーとファイル構造</h2>
これは、テーマのシンプルな（そして必須の）フォルダーとファイル構造です。

```
/bl-themes/{テーマ名}/
	languages/en.json
	metadata.json
	index.php
```

<h2 id="name-description">名前と説明</h2>
テーマの名前と説明は、JSONファイル`languages/en.json`にあります。

```
{
	"theme-data":
	{
		"name": "Hello World",
		"description": "新しいテーマです"
	}
}
```

<h2 id="information">テーマ情報</h2>
テーマの基本情報については、JSONファイル`metadata.json`に収められています。

```
{
	"author": "Bludit",
	"email": "",
	"website": "https://themes.bludit.com",
	"version": "1.0",
	"releaseDate": "2020-06-01",
	"license": "MIT",
	"compatible": "3.0",
	"notes": ""
}
```

<h2 id="examples">テーマの例</h2>
2つの例を紹介します。1つはシンプルなもの、もう1つはCSSやJavascriptのファイルを使った複雑なものです。

- [はじめてのテーマ](https://docs.bludit.com/en/themes/example-my-first-theme)
- [2番目のテーマ](https://docs.bludit.com/en/themes/example-my-second-theme)
