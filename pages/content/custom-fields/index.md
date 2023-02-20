# カスタムフィールド
<!-- position: 7 -->

<h2 id="introduction">はじめに</h2>

カスタムフィールドを使うと、ユーザーがコンテンツデータベースにフィールドを追加できます。カスタムフィールドは、コンテンツの作成や編集するときに管理パネルのインターフェイスに表示されます。

<h2 id="quick-example">簡単な例</h2>

`subtitle`という名前のカスタムフィールドを追加します。以下に移動します。

```
管理パネル > サイドバー > 設定 > 全般 > カスタムフィールド
```

以下のJSONテキストをテキストエリアに追加して「保存」ボタンをクリックします。

```json
{
    "subtitle": {
        "type": "string",
        "placeholder": "ページのサブタイトル"
    }
}
```

次に新しいページを作ります。以下に移動します。

```
管理者パネル > サイドバー > 新規コンテンツ
```

デフォルトでは、カスタムフィールドはページのオプションに表示されます。以下に移動します。

```
オプション > カスタム
```

「ページのサブタイトル」を入力するフィールドがあるので、フィールドにテキストを入力します。「オプション」ボタンをもう一度クリックしてメニューを非表示にしてタイトルとコンテンツを入力します。「保存」ボタンをクリックして新しいページを作成します。

新しいページには`subtitle`というカスタムフィールドがあり、値はテーマから表示できます。たとえば、このようにです。

```php
<?php
	echo "ページのタイトルは" . $page->title();
	echo "ページのサブタイトルは" . $page->custom('subtitle');
?>
```

<h2 id="structure">構造</h2>

構造体は、JSON形式で定義され、以下のキーをサポートします。

- `type`（必須）: カスタムフィールドのタイプ。サポートされる値(`文字列`, `ブール値`)。
- `label`（オプション）: カスタムフィールドのラベル。
- `tip`（オプション）: ユーザーがカスタムフィールドを説明するための簡単なテキスト。
- `default`（オプション）: カスタムフィールドのデフォルト値。
- `placeholder`（オプション）: フィールド内の簡単なテキスト。
- `position`（オプション）: エディター内の位置。サポートされる値（`top`, `bottom`）デフォルト値は空で**エディター > オプション > カスタム**にあるフィールドが適用されます。

<h2 id="add-custom-fields">カスタムフィールドの追加</h2>

カスタムフィールドを追加するには、次の場所に移動します。
```
管理パネル > サイドバー > 設定 > 全般 > カスタムフィールド
```

カスタムフィールドを定義するには、JSON構造の設定が必要です。以下の例をご覧ください。

カスタムフィールドを`string`、キー名を`youtube`としています

```json
{
    "youtube": {
        "type": "string",
        "label": "YouTube",
        "tip": "YouTube URLを書きます。"
    }
}
```

カスタムフィールドを`boolean`、キー名を`inStock`としています。

```json
{
    "inStock": {
        "type": "bool",
        "label": "In Stock",
        "tip": "在庫がある場合はこのフィールドを選択します。"
    }
}
```

タイプが異なる2つのカスタムフィールド。

```json
{
    "product": {
        "type": "string",
        "label": "Product",
        "tip": "製品名を入力します。"
    },
    "inStock": {
        "type": "bool",
        "label": "In Stock",
        "tip": "在庫がある場合はこのフィールドを選択します。"
    }
}
```

異なるタイプと異なるエディターの位置を持った3つのカスタムフィールド

```json
{
    "product": {
        "type": "string",
		"placeholder": "Product name",
		"position": "top"
    },
    "inStock": {
        "type": "bool",
        "tip": "在庫がある場合はこのフィールドを選択。",
		"position": "top"
    },
    "imageURL": {
        "type": "string",
		"placeholder": "Image URL",
		"position": "bottom"
    }
}
```

<h2 id="get-custom-field">カスタムフィールドの取得</h2>

クラスページには、フィールドの値を返す`custom()`メソッドがあります。

以下の例では、上の`youtube`フィールドの値を表示しています。

```php
<?php
    echo $page->custom('youtube');
?>
```

上の例から`inStock`フィールドのブール値をチェックします。

```php
<?php
    if ($page->custom('inStock')) {
        echo "在庫があります";
    } else {
        echo "在庫はありません";
    }
?>
```

<h2 id="delete-custom-field">カスタムフィールドの削除</h2>

カスタムフィールドを削除するには、エントリーをJSON構造体から削除するだけです。この場合、カスタムフィールドはデータベースから完全に削除されませんが無効になります。

すべてのカスタムフィールドを削除したい場合は、次のようにテキストエリアに空のJSONを設定してください。

```json
{}
```

<h2 id="plugin-custom-fields-parser">Custom fields parserプラグイン</h2>

このプラグインを使うと、追加のソースコード用にページコンテンツの解析ができます。

YouTubeの動画と埋め込みコードを例に説明します。

`youtube`という名前のカスタムフィールドを追加します。以下に移動します。

```console
管理パネル > サイドバー > 設定 > 全般 > カスタムフィールド
```

テキストエリアに以下のJSONテキストを追加し、「保存」ボタンをクリックします。

```json
{
    "youtube": {
        "type": "string",
        "placeholder": "Write a YouTube video embed link",
		"label": "YouTube"
    }
}
```

`Custom fields parser`プラグインを有効化します。

```console
管理パネル > サイドバー > プラグイン > Custom fields parser > 有効化
```

プラグインの設定を編集します。カスタムフィールド`youtube`用のテキストエリアがあることがわかります。カスタムフィールドに以下のiframeを追加します。

```html
<iframe width="560" height="315" src="{{ value }}" frameborder="0" allow="autoplay" allowfullscreen></iframe>
```

変数`{{value}}`には、ページで定義されたカスタムフィールドの値が含まれています。

新しいページを作成し、カスタムフィールド`youtube`にYouTubeのリンクを書き込みます。

```console
管理パネル > サイドバー > 新規コンテンツ > オプション > カスタム > YouTube
```

以下のYouTubeの埋め込みリンクを追加します。

```text
https://www.youtube.com/embed/dQw4w9WgXcQ
```

これで、ページコンテンツ内にYouTube埋め込みビデオを設定できるようになりました。

```text
こんにちは、初めてのYouTube動画です。

{{ youtube }}

ごあいさつ
```

新しいページにアクセスして、埋め込みビデオがページ内でどのように表示されるかを確認できます。これで、新しいページを作成して別のYouTubeリンクを設定しても解析によって動画埋め込みコードが表示されるようになります。

このプラグインは、埋め込みビデオがある各ページのコードの変更を回避できます。
