# GNU/Linuxへのインストール
<!-- position: 3 -->

<h2 id="ubuntu">Ubuntu 16.04 LTSへのインストール</h2>

検討事項
- PHP バージョン7.0使用。アップデートされて、あなたが使用しているバージョンと異なる場合があります。
- PHP-FPMは、ユーザー`www-data`で実行されています。
- PHP-FPMは、`unix:/run/php/php7.0-fpm.sock`上のUnixソケットでリスンしています。
- nginxは、ユーザー`www-data`で実行されています。
- ほかのWebサーバーは、インストールされていません。
- これは基本的な設定です。本番環境で使用する前に、さらに詳しい情報をご確認ください。

Nginxウェブサーバー、PHP、およびいくつかのツールをインストールします。
```
$ sudo apt install -y nginx php-fpm php-dom php-mbstring php-cli php-gd php-opcache unzip
```

Nginxを設定します。
```
$ sudo rm -f /etc/nginx/sites-enabled/*
```

バーチャルサーバーブロックを含む新しいファイルを`/etc/nginx/conf.d/bludit.conf`に追加します。
```
server {
	listen 80;
	server_name _;
	root /www/bludit;
	index index.php;

	location ~ \.php$ {
		fastcgi_pass    unix:/run/php/php7.0-fpm.sock;
		include         fastcgi.conf;
	}

	location / {
		try_files $uri $uri/ /index.php?$args;
	}
}
```

Bluditの最新バージョンをダウンロードして展開します。
```
$ mkdir /www
$ cd /www
$ curl https://www.bludit.com/releases/bludit-latest.zip --output bludit-latest.zip
$ unzip bludit-latest.zip
$ sudo chown -R www-data:www-data /www
```

サービスを再起動して、新しい構成を読み込みます。
```
$ sudo service php7.0-fpm restart
$ sudo service nginx restart
```

ブラウザを開き、http://localhostに移動してインストールを完了します。

<h2 id="centos">Centos7/Red Hat7へのインストール</h2>

検討事項
- PHP-FPMは、`nginx`ユーザーで実行されています。
- PHP-FPMは、`unix:/run/php/php-fpm.sock`上のUnixソケットでリスンしています。
- nginxは、ユーザー`nginx`で実行されています。
- ほかのWebサーバーは、インストールされていません。
- これは基本的な設定です。本番環境で使用する前に、さらに詳しい情報をご確認ください。

EPELリポジトリのインストール
```
$ sudo yum install -y epel-release
```

Nginxウェブサーバー、PHP、およびいくつかのツールをインストールします。
```
$ yum install -y nginx php-fpm php-cli php-dom php-mbstring php-zip php-gd
```

Nginxを設定します。`/etc/nginx/conf.d/bludit.conf`にバーチャルサーバーブロックを含む新しいファイルを追加します。
```
server {
	listen 80;
	server_name _;
	root /www/bludit;
	index index.php;

	location ~ \.php$ {
		fastcgi_pass    unix:/run/php/php7.0-fpm.sock;
		include         fastcgi.conf;
	}

	location / {
		try_files $uri $uri/ /index.php?$args;
	}
}
```

Bluditの最新バージョンをダウンロードして展開します。
```
$ mkdir /www
$ cd /www
$ curl https://www.bludit.com/releases/bludit-latest.zip --output bludit-latest.zip
$ unzip bludit-latest.zip
$ sudo chown -R nginx:nginx /www
```

サービスを再起動して、新しい構成を読み込みます。
```
$ sudo systemctl php-fpm restart
$ sudo systemctl nginx restart
```

ブラウザを開き、http://localhostに移動してインストールを完了します。