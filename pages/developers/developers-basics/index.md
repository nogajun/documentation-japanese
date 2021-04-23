# 開発者の基本
<!-- position: 1 -->

まず、現在インストールされているBluditの環境変数をチェックしてみましょう。管理パネルの開発者エリア`（https://www.example.com/admin/developers`）に移動します。このセクションはメニューからは見えません。

PHPの設定、`$_SERVER`などの環境変数、ロードした拡張機能、インストールしたロケール、Bluditの定数、いくつかのオブジェクトのプロパティなどの情報が表示されます。

## 管理画面へのファイル読み込みの流れ
これらのファイルは、ユーザーが管理パネルにアクセスしたときに読み込まれるファイルです。

```
index.php
	bl-kernel/boot/init.php
	bl-kernel/boot/admin.php
		bl-kernel/boot/rules/60.plugins.php
		bl-kernel/boot/rules/69.pages.php
		bl-kernel/boot/rules/99.header.php
		bl-kernel/boot/rules/99.paginator.php
		bl-kernel/boot/rules/99.themes.php
		bl-kernel/boot/rules/99.security.php
		bl-kernel/admin/themes/default/init.php
		bl-kernel/admin/controllers/{CONTROLLER}.php
		bl-kernel/admin/themes/default/index.php
			bl-kernel/admin/controllers/{VIEW}.php
```

## サイト用ファイルの読み込みの流れ
ユーザーがサイトにアクセスした際に読み込まれるファイルです。

```
index.php
	bl-kernel/boot/init.php
	bl-kernel/boot/site.php
		bl-kernel/boot/rules/60.plugins.php
		bl-kernel/boot/rules/69.pages.php
		bl-kernel/boot/rules/99.header.php
		bl-kernel/boot/rules/99.paginator.php
		bl-kernel/boot/rules/99.themes.php
		bl-kernel/boot/rules/99.security.php
		bl-themes/{THEME_NAME}/init.php
		bl-themes/{THEME_NAME}/index.php
```

## 環境変数と定数
Bludit には、あらかじめ設定されたさまざまな環境変数や定数が用意されています。

- [bl-kernel/boot/init.php](https://github.com/bludit/bludit/blob/master/bl-kernel/boot/init.php)
- [bl-kernel/boot/variables.php](https://github.com/bludit/bludit/blob/master/bl-kernel/boot/variables.php)

環境変数が定義されている場所は、rulesフォルダー`bl-kernel/boot/rules/`にもあります。たとえば、`コンテンツ`と`ページ`に関する変数は、[bl-kernel/boot/rules/69.pages.php](https://github.com/bludit/bludit/blob/master/bl-kernel/boot/rules/69.pages.php)で定義されています。
