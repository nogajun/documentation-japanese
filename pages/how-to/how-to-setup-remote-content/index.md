# リモートコンテンツプラグインの設定
<!-- position: 1 -->

Bluditは、リモートでホスティングされているコンテンツの利用をサポートしています。この例では、GitHubリポジトリのセットアップとBluditのデフォルト設定を使用したプラグイン設定について説明します。
利用例としては、[Bludit Blog](https://blog.bludit.com)は、このプラグインで動いています。サイトのコンテンツは、Githubのこちら[https://github.com/bludit/blog](https://github.com/bludit/blog)のリポジトリにあります。新しいページを作成したい場合は、そのページを作成してGithubにアップロード(push)します。

## 前提条件

 [GitHub](https://www.github.com)アカウントが必要です。無償ですぐに入手でき、無制限の公開リポジトリ*と*プライベートリポジトリが利用できます。

gitリポジトリのzip ファイルを読むための PHP [zip](https://www.php.net/manual/en/book.zip.php)モジュール。

このチュートリアルでは、[GitHub Desktop](https://desktop.github.com/)を使用してリポジトリを作成、管理します。また、BluditブログがこちらのようなURL、_https://blog.mydomain.com_にインストールされていることを前提とします。

## gitリポジトリの準備

自分のPCに、_bludit-tutorial_という名前のディレクトリを作成します。次にGitHub Desktopを開き、左上の部分をクリックして新しいリポジトリを作成します(_Add_をクリックし、_Create new repository_を選択します)。

リポジトリに_remote-content-example_と名前をつけ、簡単な説明を入力しています。_Local Path_から_bludit-tutorial_フォルダを指定し、_Create Repository_ボタンをクリックします。これで、_bludit-tutorial_フォルダーに新しいサブフォルダー_remote-content-example_が作成されます。

Bluditにコンテンツを正しく解析させるには、いくつかのフォルダを作成し次のような構造にする必要があります。

* _ルート_
   * pages
      * _ページAフォルダー_
         * index.txt
      * _ページBフォルダー_
         * index.txt
      * ...

実際には、作成したリポジトリをエクスプローラー(Windows)やFinder(MacOS)で開き下のようなフォルダーやファイルを作成します。

* remote-content-example _(すでに存在しています)_
   * pages
      * first-page
         * index.txt
      * second-page
         * index.txt

次にファイルに追加するデモコンテンツです。
_blog-content/pages/first-page/index.txt_
```markdown
# 最初のページ
<!-- date: 2018-10-10 20:00:00 -->
Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages.

このページは、リモートコンテンツサンプルの最初のページです。
```

_blog-content/pages/second-page/index.txt_
```markdown
# 2つめのページ
<!-- date: 2018-10-10 21:00:00 -->
Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages.

このページは、リモートコンテンツサンプルの2つめのページです。
```

GitHub Desktopは、あなたが行ったすべての変更を表示します。コミットメッセージとして「_最初のコミットです_」と入力して、_Commit to master_をクリックします。リポジトリを公開し(つまり、GitHubアカウントにアップロードされます)、ブラウザで_https://github.com/yourusername/remote-content-example_リポジトリを開きます。

## Bluditリモートコンテンツプラグインの有効化と設定

### Bluditプラグインの準備
Bluditの管理パネルにログインし、プラグインセクションに移動します。リモートコンテンツプラグインが表示されるまで下にスクロールします。'有効化'をクリックして、'設定'をクリックします。_webhook_入力フィールドの下に表示されているURLをコピーします。(例: _https://blog.mydomain.com/9as7dfsd98f_ )をクリップボードにコピー(_Ctrl + c_または_cmd + c_)します。

### GitHubリポジトリの設定
ウェブブラウザのタブ(またはウィンドウ)を開き、GitHubリポジトリにアクセスして_Settings_を開きます。 _Webhooks_に移動し、新しいWebhookを作成します。コピーしたWebhookのURLを_Payload URL_フィールドに貼り付け、_Content Type_を_application/json_に切り替えます。_Add webhook_をクリックします。

### Bluditにリポジトリzipファイルの場所を追加
リポジトリのメインページに戻って、_clone or download_セクションからzipパッケージのURLをコピーします。コピーした完全なURLを_Source_という名前のBluditプラグイン設定フィールドに追加します。プラグイン設定を保存します。

## 最初のpushをする
それではローカルリポジトリに戻って、新しいページを作成します。

* remote-content-example
   * pages
      * third-page
         * index.txt

_blog-content/pages/third-page/index.txt_
```markdown
# 3つめのページ
<!-- date: 2018-10-10 22:00:00 -->
Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages.

このページは、リモートコンテンツサンプルの3つめのページです。
```

先ほどと同じように変更をコミットし、リモートリポジトリにプッシュします。このあと、GitHubはwebhookを使ってBluditに変更内容を知らせます。Bluditは、設定されたパスからzipファイルを取得し、リポジトリからページを解析します。

よくできました！

## index.txtの構造
リモートコンテンツを経由してインポートされるページは、正しく解析するために次の構造に従う必要があります。

* 1行目: ページタイトル、先頭に#をつける
* そして、作成日や公開状態など提供したいすべてのメタデータをhtmlのコメント表記(`<!--`と`-->`)で囲みます。
* あなたのコンテンツ

```markdown
# これはページタイトルです
<!-- date: 2018-10-10 22:00:00 -->
<!-- put some metadata here -->
ここにあなたのコンテンツがあります
```

## 例のリポジトリとビデオチュートリアル
ビデオチュートリアルとサンプルリポジトリを用意しています。
- [リポジトリ](https://github.com/bludit/remote-content-example)

<div class="video-embed">
	<iframe width="640" height="360" src="https://www.youtube.com/embed/Kzh_Wl2ZovQ?rel=0&amp;showinfo=0" frameborder="0" gesture="media" allowfullscreen></iframe>
</div>
