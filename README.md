## AppName
 memorandum

## 概要
分野を問わず専用の話題のルーム作成したのちに、ユーザー間でのやりとりが可能。
ルームを作成することで、ユーザーの気になる話題を絞り情報の共有、収集を主な目的にする。
基本的な利用の対象は、年齢、性別等を問わず情報を集めたいと思うユーザー向けか。
上記の通りユーザーが気になる項目についてルームの作成を行い、その中で他のユーザーとの情報共有を主に行える場所の確保。

## 機能
- 新規登録・ログイン
ユーザーの管理機能実装することで次の利用の際のログインを容易にする。
<img width="1051" alt="1c6cd0667e670bedf7dc69a0d6057b1e" src="https://user-images.githubusercontent.com/79551605/117615273-72943300-b1a4-11eb-83ff-f72d86c103c4.png">
新規登録の際の項目。
<img width="1053" alt="3f37de1962a85aaf1a8fd6390bd8d200" src="https://user-images.githubusercontent.com/79551605/117615625-f2220200-b1a4-11eb-8a7c-fdc8416267c6.png">

- ルームの作成を行うことで下記の機能が使える様になる
<img width="1065" alt="c102605e6cbed02c3092fa04d11cfa11" src="https://user-images.githubusercontent.com/79551605/117617226-34e4d980-b1a7-11eb-9fb4-e47c3e1f0b75.png">

- 画像投稿機能

- コメント機能
<img width="1256" alt="d3dff39672788152756b1bef0ff8b8a8" src="https://user-images.githubusercontent.com/79551605/117617100-0666fe80-b1a7-11eb-997f-be4eb9533107.png">
- 登録の際のエラーメッセージの日本語化

##　実装予定
一度に複数の画像投稿機能

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