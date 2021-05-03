AppName
memorandum

Descriptions
写真投稿
コメント機能
新規登録/ログイン

Production
チャットルーム作成し、ユーザー間でその日の出来事を備忘録的に残して置くことが可能。




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