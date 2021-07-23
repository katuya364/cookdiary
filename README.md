# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

## usersテーブル

|Column              |Type    |Options                    |
|------------------- |------- |-------------------------- |
| nickname           | string | null: false               |
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false               |
| first_name_kanji   | string | null: false               |
| last_name_kanji    | string | null: false               |
| first_name_kana    | string | null: false               |
| last_name_kana     | string | null: false               |


### Association
- has_many :items
- has_many :messages

## itemsテーブル

|Column              |Type        |Options                         |
|------------------- |----------- |------------------------------- |
| item_name          | string     | null: false                    |
| item_description   | text       | null: false                    |
| post_data          | data       | null: false                    |
| recipe             | text       |                                |
| user               | references | null: false, foreign_key: true |

### Association
- belongs_to :user
- has_many :messages

## messagesテーブル

|Column   |Type        |Options                         |
|-------- |----------- |------------------------------- |
| content | references | null: false                    |
| user    | references | null: false, foreign_key: true |
| item    | references | null: false, foreign_key: true |

### Association
- belongs_to :user
- belongs_to :item