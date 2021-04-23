# Apache
<!-- position: 1 -->

Bluditは、システムの自動設定を試みます。インストールに問題がなければ、次の手順に進む必要はありません。

Apacheウェブサーバーは、`.htaccess`ファイルを使って、書き換えルールなどの設定を保持しています。 `.htaccess`ファイルは、隠しファイルになっています。

- ルートディレクトリにBluditをインストールする場合は、`RewriteBase/`行のコメントを解除する必要があります。
- Bluditを、例えば`bludit`のようなサブディレクトリにインストールした場合は、`RewriteBase /`のコメントを外し、`RewriteBase/bludit/`のように変更する必要があります。

以下は、`.htaccess`ファイルの例です。

```
AddDefaultCharset UTF-8

<IfModule mod_rewrite.c>

# Enable rewrite rules
RewriteEngine on

# Base directory
#RewriteBase /

# Deny direct access to the next directories
RewriteRule ^bl-content/(databases|workspaces|pages|tmp)/.*$ - [R=404,L]

# All URL process by index.php
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule ^(.*) index.php [PT,L]

</IfModule>
```
