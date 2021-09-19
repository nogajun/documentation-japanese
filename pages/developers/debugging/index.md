# デバッグ
<!-- position: 4 -->

Bluditのデバッグモードは、`/bl-kernel/boot`ディレクトリのファイル`init.php`を変更すると有効にできます。以下の部分を変更してください（11行目）。

`define('DEBUG_MODE', TRUE);`

無効にする場合。

`define('DEBUG_MODE', FALSE);`

エラーログ`debug.txt`は、`/bl-content`にあります。
