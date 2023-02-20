# 必要動作条件
<!-- position: 2 -->

PHPをサポートしたWebサーバーがあれば利用できます。

- PHP v5.6以上。
- PHP [mbstring](https://www.php.net/manual/en/book.mbstring.php)モジュール: UTF-8に必要。
- PHP [gd](https://www.php.net/manual/en/book.image.php)モジュール: 画像処理に必要。
- PHP [dom](https://www.php.net/manual/en/book.dom.php)モジュール: DOM操作に必要。
- PHP [json](https://www.php.net/manual/en/book.json.php)モジュール: JSON操作に必要。
- Bluditは、ほとんどのWebサーバーに対応しています。
    * [PHP内蔵Webサーバー](https://www.php.net/manual/en/features.commandline.webserver.php)
    * [ngx_http_rewrite_module](http://nginx.org/en/docs/http/ngx_http_rewrite_module.html)モジュールが利用可能なNginx
    * [mod_rewrite](http://httpd.apache.org/docs/current/mod/mod_rewrite.html)が利用可能なApache
    * [mod_rewrite](https://redmine.lighttpd.net/projects/1/wiki/docs_modrewrite)モジュールが利用可能なLighttpd
    * Hiawathaと[rewrite rules](https://www.hiawatha-webserver.org/howto/url_rewrite_rules)
    * H2Oは、サポートフォーラムの投稿 [H2O HTTP/2 web server and Bludit](https://forum.bludit.org/viewtopic.php?f=6&t=1015)を参照してください。
    * IISと[URL Rewrite](https://www.iis.net/downloads/microsoft/url-rewrite)については、サポートフォーラムの[こちら](https://forum.bludit.org/viewtopic.php?f=6&t=1420)の投稿をご覧ください。
