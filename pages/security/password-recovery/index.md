# パスワードの回復
<!-- position: 4 -->

`recovery.php`スクリプトを使用して、`admin`ユーザーのパスワードを回復できます。

<h2 id="how-to-recover-the-password">パスワードの回復方法</h2>

1. [recovery.php](https://raw.githubusercontent.com/bludit/password-recovery-tool/master/recovery.php)ファイルをダウンロードします。
2. `recovery.php`ファイルをBluditをインストールしたルートフォルダにアップロードします。
3. ブラウザでファイルを開きます。例: https://example.com/recovery.php `example.com`は、あなたのドメインに変えてください。
4.  `admin`ユーザーの新しいパスワードが生成され、ブラウザに表示されます。
5. 管理パネルに`admin`ユーザーでログインし、新しいパスワードを生成します。

recovery.phpスクリプトは、自分自身を削除しようとしますが、削除できない場合は、手動でrecovery.phpファイルを削除をお勧めします。

---

<h2 id="how-to-recover-the-password-via-command-line">コマンドラインからパスワードを回復</h2>

コマンドラインから`recovery.php`ファイルを実行できます。

```
# Bluditをインストールしたディレクトリに移動
cd /var/html/bludit

# ファイルをダウンロード
curl -o recovery.php https://raw.githubusercontent.com/bludit/password-recovery-tool/master/recovery.php

# ツールを実行
php recovery.php
```

```
Bludit Password Recovery Tool

Username: admin
New password: 00bef4566011d2015df2786dbd094003

>> The file recovery.php was deleted automatically for security reasons. <<
```
