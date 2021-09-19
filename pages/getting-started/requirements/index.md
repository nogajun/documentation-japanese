# 必要動作条件
<!-- position: 2 -->

PHPが利用できるWebサーバーが必要です。

- PHP v5.6以上。
- UTF-8を完全にサポートするためのPHP [mbstring](https://www.php.net/manual/en/book.mbstring.php)モジュール
- 画像を処理するためのPHP [gd](https://www.php.net/manual/en/book.image.php)モジュール
- DOM操作をするためのPHP [dom](https://www.php.net/manual/en/book.dom.php)モジュール
- JSONを操作するためのPHP [json](https://www.php.net/manual/en/book.json.php)モジュール
- Bluditは、ほとんどすべてのWebサーバーに対応しています:
   * [PHP組み込みWebサーバー](https://www.php.net/manual/en/features.commandline.webserver.php)
   * [ngx_http_rewrite_module](http://nginx.org/en/docs/http/ngx_http_rewrite_module.html)モジュールが利用可能なNginx
   * [mod_rewrite](http://httpd.apache.org/docs/current/mod/mod_rewrite.html)が利用可能なApache
   * [mod_rewrite](https://redmine.lighttpd.net/projects/1/wiki/docs_modrewrite)モジュールが利用可能なLighttpd
   * Hiawathaと[rewrite rules](https://www.hiawatha-webserver.org/howto/url_rewrite_rules)
   * H2Oは、サポートフォーラムの投稿 [H2O HTTP/2 web server and Bludit](https://forum.bludit.org/viewtopic.php?f=6&t=1015)を参照してください。
   * IISと[URL Rewrite](https://www.iis.net/downloads/microsoft/url-rewrite)については、サポートフォーラムの[こちら](https://forum.bludit.org/viewtopic.php?f=6&t=1420)の投稿をご覧ください。
