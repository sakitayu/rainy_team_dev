# README

# Rainy（仮）

## 開発チーム情報

### メンバー

- https://github.com/sakitayu
- https://github.com/kodatakasi
- https://github.com/kametmds
- https://github.com/hinokage08
- https://github.com/NakatsuboYusuke


## バージョン情報
各ソフトウェア、バージョンについては検証中

### 開発言語
- Ruby version 2.6.5

### 開発環境
- Docker version 19.03.5

### ソフトウェアフレームワーク
- Ruby on Rails API version 5.2.3
- Vue.js version 2.6.11
- Git version 2.22.0
- Node version 12.0.0
- yarn version 1.17.3

### データベース
- PostgreSQL version 11.5

### サーバー
- プラットフォーム<br>
AWS EC2
- ミドルウェア<br>
Nginx
- ストレージ<br>
AWS S3

### ドメイン
:<snip>

### API
- Facebook API
- Twitter API
- Google API
- Line API

### OS
- Mac OS 10.10〜
- Windows OS 10〜
- iOS iOS 11〜
- Android 5.0〜

### ブラウザ
- Google Chrome 最新版
- Firefox 最新版
- Safari 最新版
- Edge 最新版
- Internet Explorer バージョン 11〜


## カタログ設計

### アプリケーション名
Rainy（仮）

### アプリケーション概要
雨の日に人と人のつながりが生まれる 傘シェアリング&マッチングサービス

### コンセプト
傘の中の空間をシェアする新しい形の緩やかなマッチングサービス


## 機能一覧
機能一覧は検討中

|#|機能名|目的|重要度|備考|
|-----|-----|-----|-----|-----|
|1|ユーザー登録|ユーザー登録|検討中|メールアドレス、名前、パスワードは必須|
|2|パスワード再設定|パスワード再設定|検討中||
|3|現在地の入力|現在地の判定|検討中||
|4|傘の入力|傘を持っているかどうか判定|検討中||
|5|傘を持っているユーザー一覧表示||検討中|アカウント名を表示、今いる場所を表示、性別を表示、おおよその年齢を表示|
|6|傘を持っていないユーザー一覧表示||検討中|アカウント名を表示、今いる場所を表示、性別を表示、おおよその年齢を表示|
|7|傘を持っているユーザー検索||検討中|今いる場所から傘を持っているユーザーを検索できる、性別から傘を持っているユーザーを検索できる、年齢から傘を持っているユーザーを検索できる|
|8|ユーザー詳細表示|それぞれの一覧画面からユーザーの詳細を表示する|検討中||
|9|リクエスト送信|傘を持っていないユーザーは傘を持っているユーザーを1人選んでリクエストを送る|検討中||
|10|リクエスト承諾|傘を持っているユーザーは傘を持っていない人からきたリクエスト一覧から一つだけ選んで承諾する|検討中||
|11|マッチング|傘を持っていないユーザーからのリクエストを傘を持っているユーザーが承諾したらマッチングが完了する|検討中||
|12|メッセージ|マッチングが完了したユーザー同士でメッセージを送り合うことができる|検討中|自分のメッセージを削除することができる|
|13|プロフィール編集||検討中|自分のアカウント名を編集することができる、自分の性別を編集することができる、自分の年齢を編集することができる、自分の今いる場所を編集することができる、自分のプロフィール文を編集することができる|



## テーブル定義書
テーブル設計案

- <a href="https://bit.ly/38fZyFw" target="_blank">Created by Yuki</a>
- <a href="https://bit.ly/2R3R1Qi" target="_blank">Created by Yamazaki</a>

### テーブル論理名01
ユーザー情報

### テーブル物理名01
user

### コメント01
ユーザーの基本情報を管理する

|#|カラム論理名|カラム物理名|型|桁|NOTNULL|主キー|インデックス|コメント|
|-----|-----|-----|-----|-----|-----|-----|-----|-----|
|1|ID|id|integer|15|○|||ID|
|2|ユーザーID|uid|string|255||||ユーザーID|


### テーブル論理名02
画像情報

### テーブル物理名02
<:snip>

### コメント02
画像情報を管理する


### テーブル論理名03
ActiveStorage::Blob

### テーブル物理名03
active_storage_blob

### コメント03
画像情報のメタデータなど管理する

|#|カラム論理名|カラム物理名|型|桁|NOTNULL|主キー|インデックス|コメント|
|-----|-----|-----|-----|-----|-----|-----|-----|-----|
|1|ID|id|integer|15|○|||ID|
|2|キー|key|string|255|○||○|キー|
|3|画像名|filename|string|255|○|||画像名|
|4|MIMEタイプ|content_type|string|255||||MIMEタイプ|
|5|メタデータ|metadata|text|255||||メタデータ|
|6|サイズ|byte_size|bigint|255|○||○|サイズ|
|7|チェックサム|checksum|string|255|○|||チェックサム|


### テーブル論理名04
ActiveStorage::Attachment

### テーブル物理名04
active_storage_attachment

### コメント04
ActiveStorage::Blobと:<snip>モデルの関連付け

|#|カラム論理名|カラム物理名|型|桁|NOTNULL|主キー|インデックス|コメント|
|-----|-----|-----|-----|-----|-----|-----|-----|-----|
|1|ID|id|integer|15|○|||ID|
|2|モデル名|name|string|255|○||○|モデル名|
|3|モデル名|record_type|string|255|○||○|モデル名|
|4|外部キー|record_id|bigint|255|||○|外部キー|
|5|外部キー|blob_id|bigint|255|||○|外部キー|


## ER図
:<snip>

## サイトマップ
:<snip>

## 画面遷移図/プロトタイプ
:<snip>

## ワイヤーフレーム
:<snip>

## デザイン
:<snip>

### 色彩設計
:<snip>


## 使用予定Gem

### コア
- rails

### ミドルウェア
- pg
- puma
- unicorn

### フロントエンド
- sass-rails
- autoprefixer-rails
- ~jquery-rails~
- uglifier
- ~~slim-rails~~
- ~~html2slim~~

### バックエンド
- jbuilder
- bootsnap
- turbolinks
- rails-i18n
- ~~bcrypt~~

### 認証・ユーザー管理
- devise
- omniauth
- omniauth-facebook
- omniauth-twitter
- omniauth-google
- omniauth-line
- activeadmin

### API
- aws-sdk-s3

### デバッグ
- pry-rails
- better_errors
- binding_of_caller

### テスト (RSpec)
- factory_bot_rails
- spring-commands-rspec
- rspec-rails
- database_cleaner
- webdrivers

### テスト・開発環境
- byebug
- web-console
- listen
- spring
- spring-watcher-listen
- capybara
- selenium-webdriver
- tzinfo-data
- faker

## チェンジログ
変更があった場合、随時チェンジログを記載する。

- 20/01/10 version 1.0 を作成
- 20/01/17 version 1.1<br>
  仕様策定用にアップロード
