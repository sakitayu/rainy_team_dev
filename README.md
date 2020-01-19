# README
This Repository is Development for Rainy for Students(仮)

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
- Ruby v2.6.5

### 開発環境
- Docker v19.03.5

### ソフトウェアフレームワーク
- Ruby on Rails API v5.2.3
- Vue.js v2.6.11
- Git v2.22.0
- Node v12.0.0
- yarn v1.17.3

### データベース
- PostgreSQL v11.5

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
- LINE API
- Maps JavaScript API

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
- Internet Explorer v11~


## カタログ設計

### アプリケーション名
Rainy for Students(仮)

### アプリケーション概要
雨の日に人と人のつながりが生まれる 傘シェアリング&マッチングサービス

### コンセプト
傘の中の空間をシェアする新しい形の緩やかなマッチングサービス


## 機能一覧
機能一覧は検討中

|#|機能名|目的|重要度|備考|
|-----|-----|-----|-----|-----|
|1|ユーザー登録機能|ユーザーをフィルタリングしたり制限する|高||
|2|SNSログイン機能|ユーザーをSNS経由でログインさせる|高|Facebook, Twitter, Google, LINE|
|3|傘の所有機能|ユーザーが傘を持っている/持っていないを判定する|高||
|4|現在地表示機能|ユーザーの位置情報を地図上で表示する|高|Maps JavaScript API|
|5|マイページ機能|ユーザーのプロフィールの設定、他人のページを閲覧する|高||
|6|ステータス機能|ユーザーがログインしているかどうか表示する|高||
|7|決済機能|ユーザーの支払い情報を登録する|低||
|8|傘持ちユーザー目的地/到着地の入力|傘を持っていないユーザーは目的地と到着地を入力する|高||
|9|傘なしユーザー目的地/到着地の入力|傘を持っているユーザーは目的地と到着地を入力する|高||
|10|相合傘リクエスト機能|傘を持っていないユーザーが一覧に表示されたユーザーへリクエストを送る|高||
|11|相合傘レスポンス機能|傘を持っているユーザーがリクエストを承諾/拒否する|高||
|12|相合傘マッチング通知機能|相合傘マッチング通知機能|高||
|13|到着の通知機能|マッチングしたユーザー同士が目的地に到着したら、通知を送る|中||
|14|チャット機能|ユーザー同士が連絡する|高||
|15|チャットの未読/既読機能|チャットの未読/既読を判定する|高||
|16|お礼機能|マッチングしたユーザー同士がお礼を送れる(当日限定)|中||
|17|ユーザー評価機能|ユーザーをスコア化する、マイページにステータスを表示する|中||
|18|ユーザーミュート機能|不快なユーザーとのマッチングをなくす|中||
|19|傘持ちユーザー一覧表示機能|傘を持っているユーザーは傘を持っていないユーザーの一覧を見れる|高||
|20|傘なしユーザー一覧表示機能|傘を持っていないユーザーは傘を持っているユーザーの一覧を見れる|高||
|21|距離順ユーザー一覧ソート機能|傘を持っていない人は距離が近い人順にユーザーをソートする|中||
|22|高スコアユーザー一覧ソート機能|高スコア順にユーザーをソートする|中||
|23|天気お知らせ機能|雨に日の前日にユーザーに天気予報を通知をする|低||
|24|||||


## テーブル定義書
テーブル設計案

- <a href="https://bit.ly/38fZyFw" target="_blank">Created by Yuki</a>
- <a href="https://bit.ly/2R3R1Qi" target="_blank">Created by Yamazaki</a>

### テーブル論理名01
ユーザー情報

### テーブル物理名01
users

### コメント01
ユーザーの基本情報を管理する

|#|カラム論理名|カラム物理名|型|桁|NOTNULL|主キー|インデックス|コメント|
|-----|-----|-----|-----|-----|-----|-----|-----|-----|
|1|ID|id|integer|15|○||||
|2|管理者権限|admin|boolean|false|○||||
|3|名前|name|string|255|○||||
|4|メールアドレス|email|string|255|○||||
|5|パスワード|password|string|255|○||||
|6|年齢|age|integer|15|○|||select|
|7|性別|sex|integer|15|○|||radio|
|8|大学名|unversity|string|255|○|||select|
|9|学年|grade|integer|15||||select|
|10|ポイント|point|integer|15|||||
|11|評価|valuation|integer|15||||五つ星で評価|
|12|傘所持有無|umbrella|boolean|||||radio|
|13|緯度|longitude|integer||||||
|14|経度|latitude|integer||||||
|15|プレミアム会員|premium|boolean|false|||||
|16|画像|image|text|255|||||


### テーブル論理名02
ActiveStorage::Blob

### テーブル物理名02
active_storage_blob

### コメント02
画像情報のメタデータなど管理する

|#|カラム論理名|カラム物理名|型|桁|NOTNULL|主キー|インデックス|コメント|
|-----|-----|-----|-----|-----|-----|-----|-----|-----|
|1|ID|id|integer|15|○||||
|2|キー|key|string|255|○||○||
|3|画像名|filename|string|255|○||||
|4|MIMEタイプ|content_type|string|255|||||
|5|メタデータ|metadata|text|255|||||
|6|サイズ|byte_size|bigint|255|○||○||
|7|チェックサム|checksum|string|255|○||||


### テーブル論理名03
ActiveStorage::Attachment

### テーブル物理名03
active_storage_attachment

### コメント03
ActiveStorage::Blobとuserモデルの関連付け

|#|カラム論理名|カラム物理名|型|桁|NOTNULL|主キー|インデックス|コメント|
|-----|-----|-----|-----|-----|-----|-----|-----|-----|
|1|ID|id|integer|15|○|||ID|
|2|モデル名|name|string|255|○||○|モデル名|
|3|モデル名|record_type|string|255|○||○|モデル名|
|4|外部キー|record_id|bigint|255|||○|外部キー|
|5|外部キー|blob_id|bigint|255|||○|外部キー|


### テーブル論理名04
マッチング

### テーブル物理名04
matchings

### コメント04
マッチング機能

|#|カラム論理名|カラム物理名|型|桁|NOTNULL|主キー|インデックス|コメント|
|-----|-----|-----|-----|-----|-----|-----|-----|-----|
|1|ID|id|integer|15|○|||ID|
|2|フォロー(申請者)|follower|integer|15|||○||
|3|フォロー(承諾者)|followed|integer|15|||○||


### テーブル論理名05
メッセージ

### テーブル物理名05
messages

### コメント05
チャット機能

|#|カラム論理名|カラム物理名|型|桁|NOTNULL|主キー|インデックス|コメント|
|-----|-----|-----|-----|-----|-----|-----|-----|-----|
|1|ID|id|integer|15|○|||ID|
|2|チャット本文|content|text|255|||||
|3|ユーザーID|user_id|integer|15|||○||
|4|ルームID|room_id|integer|15|||○||


### テーブル論理名06
ルーム

### テーブル物理名06
rooms

### コメント06
チャット機能

|#|カラム論理名|カラム物理名|型|桁|NOTNULL|主キー|インデックス|コメント|
|-----|-----|-----|-----|-----|-----|-----|-----|-----|
|1|ID|id|integer|15|○|||ID|
|2|ユーザーID|user_id|integer|15|||○||
|3|ルームID|room_id|integer|15|||○||


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
- jquery-rails
- uglifier
- ~~slim-rails~~
- ~~html2slim~~

### バックエンド
- jbuilder
- bootsnap
- turbolinks
- rails-i18n
- ~~bcrypt~~
- ransack

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
- 20/01/19 version 1.2<br>
  仕様策定を更新
