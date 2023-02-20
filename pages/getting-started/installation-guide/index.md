# インストールガイド
<!-- position: 3 -->

<h2 id="installation-from-zip-file">ZIPファイルからインストール</h2>

1. [公式ページ](https://www.bludit.com)からBludit最新版をダウンロードします。
2. zipファイルを展開します。
3. 展開したファイルをサーバーやホスティング先にアップロードします。ファイルは、ルートディレクトリや`/bludit/`などのサブディレクトリにアップロードできます。
4. ファイルのアップロードにはFTPクライアント、WebFTP、またはホスティング会社が提供するツールを使います。
5. ドメインにアクセスします。ルートディレクトリにアップロードした場合は、`https://www.example.com`、サブディレクトリにアップロードした場合は`https://www.example.com/bludit/`に移動します。
6. BluditインストーラーにしたがってWebサイトを設定します。

---

<h2 id="subdirectory">サブディレクトリへのインストール</h2>

Bluditをサブディレクトリにインストールする場合、インストールディレクトリにある`.htaccess`ファイルの変更が必要になる場合があります。

たとえば、サブディレクトリ`bludit`にBluditがインストールされている場合、`.htaccess`ファイルを以下のように変更する必要があります（9行目）。

```
# Base directory
RewriteBase /bludit/
```

---

<h2 id="php-built-in-web-server">PHP内蔵Webサーバーを利用する</h2>

 [PHPに内蔵されたWebサーバー](https://www.php.net/manual/en/features.commandline.webserver.php)を使うとコマンドラインからBluditを手早く実行できます。

```
$ git clone https://github.com/bludit/bludit.git
$ cd bludit
$ php -S localhost:8000
```

好きなブラウザでURL `http://localhost:8000`にアクセスします。

---

<h2 id="docker">Dockerを利用する</h2>

Bludit公式[Dockerイメージ](https://hub.docker.com/r/bludit/docker/)を使っても実行できます。

```
$ docker run --name bludit -p 8000:80 -d bludit/docker:latest
```

好きなブラウザでURL `http://localhost:8000`にアクセスします。

---

<h2 id="vagrant">Vagrantの利用</h2>

Vagrantを使って公式[Vagrantビルド](https://pilab.dev/bludit-vagrant)からも実行できます。

```
$ git clone https://github.com/mhancoc7/Bludit-Vagrant.git
$ cd Bludit-Vagrant
$ vagrant up
```

好きなブラウザでURL `http://localhost:8000`にアクセスします。

---

<div class="note">
<div class="title">Web サーバーについて</div>
追加の設定については、Webサーバーについての章をご覧ください。<a href="../../webservers/apache">Apache</a> - <a href="../../webservers/nginx">Nginx</a>
</div>
