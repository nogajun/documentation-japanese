# 管理パネルURLを変更する
<!-- position: 3 -->

Bludit管理パネルは、デフォルトでは`/admin/`フォルダにあります。

これを変更するには、`/bl-kernel/boot/variables.php`ファイルを編集します。`ADMIN_URI_FILTER`を設定したい名前に変更してください。

<pre><code data-language="php">define('ADMIN_URI_FILTER', 'admin');</code></pre>
