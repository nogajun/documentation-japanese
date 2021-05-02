# プラグインとページ
<!-- position: 11 -->

プラグインを使ってページのすべてのフィールドを変更できます。

## ページ内容を変更
下のコードは、プラグインでページ内容を変更する方法です。

```
<?php
class ModContent extends Plugin {

    // このフックはページがすでに設定されている場合にロードされます
    function beforeSiteLoad() {
        global $content;

        // 読み込まれたページごとに、そのページのコンテンツを変更する
        foreach ($content as $key=>$page) {
            // ページコンテンツを取得
            $pageContent = $page->contentRaw();

            // 文字列を検索して置換
            $newPageContent = str_replace("<!-- Dynamic -->", "Dynamic content", $pageContent);

            // 新しいページのコンテンツを設定
            $page->setField('content', $newPageContent);
        }
    }
}
?>
```

このプラグインは、`beforeSiteLoad`フック(ユーザーがコンテンツを見る前に実行されます)を実行した後、`<! -- Dynamic -- >`文字列を検索し、それを`Dynamic content`文字列に置き換えてコンテンツを変更します。


## ページタイトルを変更
下のコードは、プラグインを使用してページタイトルを変更します。

```
<?php
class ModTitle extends Plugin {

    // このフックはページがすでに設定されている場合にロードされます
    function beforeSiteLoad() {
        global $content;

        // 読み込まれたページごとに、ページのタイトルを変更する
        foreach ($content as $key=>$page) {
            // ページタイトルを取得
            $title = $page->title();

            // ページ作成日を取得
            $date = $page->date();

            // タイトルと日付を連結する
            $newTitle = $title.' '.$date;

            // 新しいタイトルを設定
            $page->setField('title', $newTitle);
        }
    }
}
?>
```

プラグインは、`beforeSiteLoad`フック(ユーザーがコンテンツを見る前に実行される)を実行し、ページタイトルを現在のタイトルと作成日に変更します。
