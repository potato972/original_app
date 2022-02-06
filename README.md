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

# テーブル設計

## users テーブル

| Column                | Type   | Option                   |
| --------------------- | ------ | ------------------------ |
| name                  | string | null:false               |
| email                 | string | null:false, unique: true |
| password              | string | null:false               |
| password_confirmation | string | null:false               |

### Association

- has_many :tweets
- has_many :comments


## tweets テーブル

| Column   | Type       | Option                        |
| -------- | ---------- | ----------------------------- |
| text     | string     | null:false                    |
| keyword  | string     | null:false                    |
| nickname | string     | null:false                    |
| user     | references | null: false, foreign_key:true |

### Association

- has_many :comments
- belongs_to :user


## comments テーブル

| Column  | Type       | Option                        |
| ------- | ---------- | ----------------------------- |
| comment | string     | null:false                    |
| user    | references | null: false, foreign_key:true |
| tweet   | references | null: false, foreign_key:true |

### Association

belongs_to :tweet
belongs_to :user
