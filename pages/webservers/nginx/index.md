# Nginx
<!-- position: 2 -->

Bluditは[Nginx](https://nginx.org/en/)をサポートしており、実際にウェブサーバーとして推奨しています。

Bluditには、すべてのリクエストとレスポンスを処理する独自の`ルーター`を持っています。すべてのリクエストを`index.php`ファイルにリダイレクトするというアイデアです。

検討事項
- Webサーバでは、CGIプロセスマネージャとしてPHP-FPMが動作している。
- PHP-FPMは、Unixソケットの`unix:/run/php/php-fpm.sock`で待ち受けている。

## HTTPの設定
Bludit用の新しいサーバーブロックを設定するには、新規ファイルとして`/etc/nginx/conf.d/bludit.conf`を作成し、設定します。このディレクトリは、GNU/Linuxの他のディストリビューションでは異なる場合があります。例えばUbuntuでは、`/etc/nginx/sites-enabled/bludit.conf`になります。

セキュリティ上の理由から `/bl-kernel/` 、 `/bl-content/databases` 、 `/bl-content/pages` 、 `/bl-content/workspaces` フォルダーのPHPファイルへのアクセスを禁止することも忘れないでください。そうしない場合、これらのディレクトリにあるいくつかのファイルにユーザーが直接アクセスしてしまう可能性があります。

```
server {
	listen 80;
	server_name example.com;
	root /www/bludit;
	index index.php;

	access_log /var/log/nginx/example.log;
	error_log /var/log/nginx/example.log;

	location ~ \.(jpg|jpeg|gif|png|css|js|ico|svg|eot|ttf|woff|woff2|otf)$ {
		access_log        off;
		expires           30d;
	}

	location ~ \.php$ {
		fastcgi_pass    unix:/run/php/php-fpm.sock;
		fastcgi_index   index.php;
		include         fastcgi.conf;
	}

	location / {
		try_files $uri $uri/ /index.php?$args;
	}

	location ^~ /bl-content/databases/ { deny all; }
	location ^~ /bl-content/workspaces/ { deny all; }
	location ^~ /bl-content/pages/ { deny all; }
	location ^~ /bl-kernel/*.php { deny all; }
}
```

## HTTPSの設定
HTTPSの設定には追加の設定が必要です。また、当然ですがSSL証明書も必要です。[LetsEncrypt](https://letsencrypt.org)を使用して、無償の証明書取得をお勧めします。

サーバーブロックは以下の設定を使用しています。設定ではリクエストをHTTPからHTTPSにリダイレクトするためのブロックを追加しています。
```
server {
	listen 443 ssl;
	server_name example.com;
	root /www/bludit;
	index index.php;

	access_log /var/log/nginx/example.log;
	error_log /var/log/nginx/example.log;

	ssl_certificate         /etc/letsencrypt/live/example.com/fullchain.pem;
	ssl_certificate_key     /etc/letsencrypt/live/example.com/privkey.pem;
	ssl_dhparam             /etc/ssl/certs/dhparam.pem;

	ssl_session_cache       shared:SSL:50m;
	ssl_session_timeout     10m;

	ssl_prefer_server_ciphers	on;
	ssl_stapling			on;
	ssl_stapling_verify		on;
	ssl_protocols			TLSv1.1 TLSv1.2;
	ssl_ciphers			"ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:DHE-RSA-AES256-SHA256:DHE-RSA-AES128-SHA256:DHE-RSA-AES256-SHA:DHE-RSA-AES128-SHA:ECDHE-RSA-DES-CBC3-SHA:EDH-RSA-DES-CBC3-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:DES-CBC3-SHA:HIGH:!aNULL:!eNULL:!EXPORT:!DES:!MD5:!PSK:!RC4";

	add_header Strict-Transport-Security "max-age=31557600; includeSubDomains";

	location ~ \.(jpg|jpeg|gif|png|css|js|ico|svg|eot|ttf|woff|woff2|otf)$ {
		access_log        off;
		expires           30d;
	}

	location ~ \.php$ {
		fastcgi_pass    unix:/var/run/php-fpm/php-fpm.sock;
		fastcgi_index   index.php;
		include         fastcgi.conf;
		fastcgi_param   HTTPS on;
	}

	location / {
		try_files $uri $uri/ /index.php?$args;
	}

	location ^~ /bl-content/databases/ { deny all; }
	location ^~ /bl-content/workspaces/ { deny all; }
	location ^~ /bl-content/pages/ { deny all; }
	location ^~ /bl-kernel/*.php { deny all; }
}

# Redirect from HTTP to HTTPS
server {
	listen 80;
	server_name example.com;
	return 301 https://www.example.com$request_uri;
}
```
