# Raspberry Piへ簡単インストール
<!-- position: 2 -->

このプロジェクトの目的は、Raspberry PiにBluditを設定しインストールする簡単な方法を作ることです。

このビルドスクリプトは[Pi Lab](https://pilab.dev/bludit-pi)から提供されています。

> ***このスクリプトは、すでにWebサーバがインストールされ構成されているRaspberry Pi上で実行することはお勧めしません。***

以下のテクノロジーが自動的にインストールされます。
* Apache
* PHP
* [Bludit](https://www.bludit.com/) (最新版)

## インストール準備
1. Raspberry Piと[Raspbian](https://www.raspberrypi.org/downloads/raspbian/)
2. Gitがインストール済み

```
sudo apt-get install git
```

## インストール手順
1. Raspberry Piで、このリポジトリをインストールする適当なディレクトリを探します。

2. 以下を実行します。
```
git clone https://github.com/mhancoc7/Bludit-Pi.git
```
3. 以下を実行します。
```
cd Bludit-Pi
```
4. 以下を実行します。
```
bash build.sh
```

## 使用方法
1. 設定作業が完了していることを確認してください
2. ウェブブラウザをhttp://raspberrypi.local (またはRPiのホスト名に設定されているもの) にアクセスしてBluditサイトを表示します。
3. 手順に従ってBluditのインストールを完了します。

## アップグレード
以下を実行します。
```
bash build.sh
```

> #### *アップグレードすると、Bludit に加えた設定変更がすべて削除されることに注意してください。Bludit管理パネルで適用した内容や設定は上書きされません。*

## メモ
ウェブブラウザで Bluditを読み込む際にエラー メッセージが表示される場合は、何らかの理由でビルドプロセスの手順が失敗したことが考えられます。ビルドは再度実行しても問題ありません。

## 免責事項
すべてのコードは現状のまま提供され、いかなる保証もありません。ご自身の責任でご利用ください。

---

[<img src="https://pilab.dev/images/check-it-out-on-github.png" alt="GitHubで入手" width="300px;" />](https://github.com/mhancoc7/Bludit-Pi/)
