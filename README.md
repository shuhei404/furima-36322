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

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| name               | string | null: false |
| email              | string | null: false |
| encrypted_password | string | null: false |
| name_kanji         | string | null: false |
| name_kana          | string | null: false |
| birth_day          | string | null: false |

### Association

- has_many :items
- has_many :purchase_records

## items テーブル

| Column              | Type       | Options                        |
| --------------------| ---------- | -------------------------------|
| image               | text       | null: false                    |
| name                | string     | null: false                    |
| category            | string     | null: false                    |
| status              | string     | null: false                    |
| delivery_fee        | string     | null: false                    |
| shipping_area       | string     | null: false                    |
| shipping_date       | string     | null: false                    |
| selling_price       | string     | null: false                    |
| sales_commission    | string     | null: false                    |
| sales_profit        | string     | null: false                    |
| user                | references | null: false, foreign_key: true |


### Association

- belongs_to :user
- has_one :purchase_records


## purchase_record テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| user   | references | null: false, foreign_key: true |
| item   | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :item
- has_one :delivery_address



## delivery_address テーブル

| Column              | Type       | Options                        |
| ------------------- | ---------- | ------------------------------ |
| post_code           | string     | null: false                    |
| prefectures         | string     | null: false                    |
| municipalities      | string     | null: false                    |
| address             | string     | null: false                    |
| building_name       | string     |                    |
| telephone_number    | string     | null: false                    |
| purchase_record     | references | null: false, foreign_key: true |

### Association

- belongs_to :purchase_records
