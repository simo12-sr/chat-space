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
|Column|Type|Options|
|------|----|-------|
|name.index:true|text|null: false|
|e_mail|text|null: false|
|password|text|null: false|

### Association
- has_many :groups, through: :group_users
- has_many :messages
- has_many :group_users

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|text|null: false|

### Association
has_many :users, through: :group_users
has_many :messages
has_many :group_users

## messageテーブル
|Column|Type|Options|
|------|----|-------|
|body|text|
|image|string|
|group|references|null: false, foreign_key: true|
|users|references|null: false, foreign_key: true|

### Association
belongs_to :group
belongs_to :user

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user|references|null: false, foreign_key: true|
|group|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user