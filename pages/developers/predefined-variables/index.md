# 定義済み変数
<!-- position: 3 -->

Bludit には、開発者を支援するために定義済み変数が用意されています。

<h2 id="content">$content</h2>

`$content`変数は、公開されたすべてのページ(`ページ`および`固定ページ`を含むが`静的ページ`は含まない)を含む配列です。配列に含まれる各ページは[Page Object](https://github.com/bludit/bludit/blob/master/bl-kernel/pagex.class.php)です。

配列は、`date`または`position`の順に並んでいますが、この動作はシステムの設定で変更できます。

この変数をどのように扱うかについては、コードスニペットを参照してください。
- [https://docs.bludit.com/en/dev-snippets/content-pages](../../dev-snippets/content-pages/)

<h2 id="staticContent">$staticContent</h2>

`$staticContent`変数は、すべての`静的ページ`を含む配列です。配列に含まれる各ページは[Page Object](https://github.com/bludit/bludit/blob/master/bl-kernel/pagex.class.php)です。

配列は設計上、`position`順に並んでいます。

この変数をどのように扱うかについては、コードスニペットを参照してください。
- [https://docs.bludit.com/en/dev-snippets/content-static](../../dev-snippets/content-static/)

<h2 id="page">$page</h2>

`$page`変数は、ユーザーが参照しているページを表します。変数は[Page Object](https://github.com/bludit/bludit/blob/master/bl-kernel/pagex.class.php)です。

たとえば、ユーザーが`https://www.example.com/my-dog-rules`を参照している場合、`$page`変数にはキーのページオブジェクト(`my-dog-rules`など)が入ります。

<h2 id="pages">$pages</h2>

`$pages`変数は[Pages Object](https://github.com/bludit/bludit/blob/master/bl-kernel/pages.class.php)です。このオブジェクトは、ページデータベースを操作のために使われます。

<h2 id="tags">$tags</h2>

`$tags`変数は[Tags Object](https://github.com/bludit/bludit/blob/master/bl-kernel/tags.class.php)です。このオブジェクトは、タグデータベースを操作のために使われます。

<h2 id="categories">$categories</h2>

`$categories`変数は[Categories Object](https://github.com/bludit/bludit/blob/master/bl-kernel/categories.class.php)です。このオブジェクトは、カテゴリーデータベースを操作のために使われます。
