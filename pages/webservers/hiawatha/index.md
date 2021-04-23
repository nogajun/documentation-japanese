# Hiawatha
<!-- position: 3 -->

Bluditは、Hiawathaウェブサーバをサポートしています。よりよい結果のためには、以下のようなリライトルールを使用するとよいでしょう。

```
UrlToolkit {
    ToolkitID = bludit
    RequestURI exists Return
    Match [^?]*(\?.*)? Rewrite /index.php$1
}
```
