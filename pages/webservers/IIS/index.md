# インターネット インフォメーション サービス(IIS)
<!-- position: 4 -->

Bluditは、厳密にはこのプラットフォームで動作するように設計されていませんが、適切な設定を行えば、[PHP](https://docs.microsoft.com/en-us/iis/application-frameworks/scenario-build-a-php-website-on-iis/configuring-step-1-install-iis-and-php)5.6+を実行するIIS Webサーバ上でWebExtモジュール[URL Rewrite](https://www.iis.net/downloads/microsoft/url-rewrite)を使用してBluditをホストすることができます。

まず、必要な書き換えルールを保存しているApacheの`.htaccess`ファイルを、対応する`web.config`ファイルに変換する必要があります。

```
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <system.webServer>
        <rewrite>
            <rules>
                <rule name="Rule1" stopProcessing="true">
                    <match url="^bl-content/x(.*)\.txt$" ignoreCase="false" />
                    <action type="Redirect" url="{R:0}" redirectType="Temporary" />
                </rule>
                <rule name="Rule2" stopProcessing="true">
                    <match url="^(.*)" ignoreCase="false" />
                    <conditions logicalGrouping="MatchAll">
                        <add input="{REQUEST_FILENAME}" matchType="IsFile" ignoreCase="false" negate="true" />
                    </conditions>
                    <action type="Rewrite" url="index.php" />
                </rule>
            </rules>
        </rewrite>
    </system.webServer>
</configuration>
```

次に、IISサービスアカウント(通常は`IUSR`)に`bl-content`フォルダーのフルコントロールの許可を有効にします。

それ以外の部分は、すぐに使えるはずです。