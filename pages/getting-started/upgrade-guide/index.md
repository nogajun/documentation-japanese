# アップグレードガイド
<!-- position: 4 -->

<h2 id="upgrade-from-major-version">同一メジャーバージョンからのアップグレード</h2>

この手順は、同じメジャーバージョンのBluditから任意のバージョンにアップグレードする場合に有効です。メジャーバージョンとはバージョン番号の最初の桁のことで、例としては`Bludit v3.x`の3の部分です。

1. すべてのファイルとディレクトリを含む完全なバックアップを取ります。
2. ロールバックに備えて、使用しているBluditのバージョンを控えておいてください。
3. Bludit最新版を[公式ページ](https://www.bludit.com)からダウンロードします。
4. zipファイルを展開します。
5. 既存のファイルを新しいファイルで置き換えます。
6. ブラウザのキャッシュを消去して、下の注意事項を読みます。
7. 管理パネルにログインして設定を確認します。
8. これで完了です。

> 注意: ウェブサイトがサーバーキャッシュシステムに守られている場合(例えばCloudflareは、デフォルトでキャッシュを提供しています)、そこにあるファイルも消去の必要があります。また、ブラウザーのキャッシュをクリアすることもお勧めします。Bluditは、新しいファイルがあればファイルを再読み込みしますが、TinyMCEのようないくつかのコンポーネントでは再読み込みができずUIに問題を起こしたり、JavaScriptのエラーを起こす場合があります。

---

<h2 id="upgrade-from-bludit-2-to-bludit-3">Bludit v2.3.4からBludit v3.0へのアップグレード</h2>

メジャーバージョン間の移行には、@anaggh氏が作成したツールの利用をお薦めします。以下の注意事項と彼のリポジトリで説明されている移行手順もお読みください。何か質問があれば、[フォーラム](https://forum.bludit.org)や[チャット](https://gitter.im/bludit/support)でお尋ねください。

### 移行前の検討事項

- 移行を始める前には、フルバックアップを取ることを忘れないでください。フルバックアップとは、`bl-content`フォルダ内のファイルだけでなく、すべてのファイルをコピーするという意味です。
- `Backups`と`Timemachine X`プラグインは無効化され、コンテンツは削除されます。
- マイグレーションツールは、`/migrations/`というフォルダーを作成します。そして、その中にはBludit v3.0と互換性のあるすべてのページとデータベースが収められた`bl-content`というフォルダを作成します。
- 移行プロセス終了後は、`/migrations/`を除く、すべてのファイルとフォルダーを削除し、新しいバージョンのBluditをインストールする必要があります。
- Bludit v3.0インストール後、新しくインストールしたBluditに`/migrations/bl-content`フォルダーをコピーします。

https://github.com/bludit-plugins/migration-v2-to-v3/blob/main/migrate.php
