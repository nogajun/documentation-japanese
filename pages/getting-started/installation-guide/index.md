# インストールガイド
<!-- position: 3 -->

<h2 id="installation-from-zip-file">ZIPファイルからインストール</h2>

1. Bludit最新版を[公式ページ](https://www.bludit.com)からダウンロードします。
2. zipファイルを展開します。
3. 展開したファイルをサーバーやホスティング先にアップロードします。ファイルは、ルートディレクトリ、または`/bludit/`などのサブディレクトリにアップロードできます。
4. ファイルをアップロードするには、FTPクライアント、WebFTP、またはホスティング会社が提供するツールを使います。
4. ドメインにアクセスします。ルートディレクトリにアップロードした場合は、`https://www.example.com`に、サブディレクトリにアップロードした場合は`https://www.example.com/bludit/`に移動します。
5. Bluditインストーラーに従ってWebサイトを設定します。

---

<h2 id="subdirectory">サブディレクトリへのインストール</h2>

Bluditをサブディレクトリにインストールする場合、インストールディレクトリにあるファイル`.htaccess`を変更の必要がある場合があります。

たとえば、Bluditがサブディレクトリ`bludit`にインストールされている場合、`.htaccess`ファイルを以下のように変更の必要があります(9行目)。

```
# Base directory
RewriteBase /bludit/
```

---

<h2 id="php-built-in-web-server">PHP組み込みWeb サーバーの利用</h2>

 [PHP組み込みのWebサーバー](https://www.php.net/manual/en/features.commandline.webserver.php)を使うとコマンドラインからBluditを素早く実行できます。

```
$ git clone https://github.com/bludit/bludit.git
$ cd bludit
$ php -S localhost:8000
```

好きなブラウザでURL `http://localhost:8000`にアクセスします。

---

<h2 id="docker">Dockerの利用</h2>
Bluditを公式  [Dockerイメージ](https://hub.docker.com/r/bludit/docker/) から実行します。

```
$ docker run --name bludit -p 8000:80 -d bludit/docker:latest
```

好きなブラウザでURL `http://localhost:8000`にアクセスします。

---

<h2 id="vagrant">Vagrantの利用</h2>
Vagrantを使って公式[Vagrantビルド](https://pilab.dev/bludit-vagrant)から実行します。

```
$ git clone https://github.com/mhancoc7/Bludit-Vagrant.git
$ cd Bludit-Vagrant
$ vagrant up
```

好きなブラウザで、URL `http://localhost:8000`にアクセスします。


---

<div class="note">
<div class="title">Web サーバーについて</div>
追加の設定については、Webサーバーについての章をご覧ください。<a href="../../webservers/apache">Apache</a> - <a href="../../webservers/nginx">Nginx</a>
</div>
