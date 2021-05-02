# Hiawatha
<!-- position: 3 -->

Bluditは、Hiawathaウェブサーバーをサポートしています。よりよい結果のために、以下のようなリライトルールを使用するとよいでしょう。

```
UrlToolkit {
    ToolkitID = bludit
    RequestURI exists Return
    Match [^?]*(\?.*)? Rewrite /index.php$1
}
```
