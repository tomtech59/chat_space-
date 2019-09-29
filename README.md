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

## Usersテーブル
|column|type|options|
|------|----|-------|
|name|string|null: false, index: true|
|email|string|null: false, unique: true|
|password|string|null: false|

### Association
- has_many :Gropus_Users
- has_many :Groups, through: :Gropus_Users
- has_many :Messages

## Messagesテーブル
|column|type|options|
|------|----|-------|
|text|string|null: false|
|image|string|
|User_id|references|null: false, foreign_key: true|
|Group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :User
- belongs_to :Group

## Groupsテーブル
|column|type|options|
|------|----|-------|
|name|string|null: false|

### Association
- has_many :Groups_Users
- has_many :Users, through: :Groups_Users
- has_many :Messages

## Gropus_Usersテーブル
|column|type|options|
|------|----|-------|
|Group_id|integer|null: false, foreign_key: true|
|User_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :User
- belongs_to :Group