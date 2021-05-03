## AppName
 memorandum

## 概要
分野を問わず専用の話題のルーム作成したのちに、ユーザー間でのやりとりが可能。
ルームを作成することで、ユーザーの気になる話題を絞り情報の共有、収集を主な目的にする。


## 機能
- 新規登録・ログイン
<img width="1440" alt="スクリーンショット 2021-05-03 16 08 30" src="https://user-images.githubusercontent.com/79551605/116850451-a5ca4580-ac2b-11eb-9edf-931d163aac0b.png">
<img width="1440" alt="スクリーンショット 2021-05-03 16 18 27" src="https://user-images.githubusercontent.com/79551605/116850433-9e0aa100-ac2b-11eb-9d0b-67cab46ceb44.png">
- 画像投稿機能（複数枚）⇦実装中
- コメント機能
- 登録の際のエラーメッセージの日本語化


## 本番環境
上記機能実装後記載

## 開発環境
開発環境
Ruby/Ruby on Rails/MySQL/Github/Visual Studio Code


## users テーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| name     | string | null: false |
| email    | string | null: false |
| password | string | null: false |


- has_many :room_users
- has_many :rooms, through: room_users
- has_many :messages



## rooms テーブル

| Column | Type   | Options     |
| ------ | ------ | ----------- |
| name   | string | null: false |


- has_many :room_users
- has_many :users, through: room_users
- has_many :messages

## room_users テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| user   | references | null: false, foreign_key: true |
| room   | references | null: false, foreign_key: true |

- belongs_to :room
- belongs_to :user



## messages テーブル


| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| content | string     |                                |
| user    | references | null: false, foreign_key: true |
| room    | references | null: false, foreign_key: true |


- belongs_to :room
- belongs_to :user