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

|column|type|options|
|------|----|-------|
|name|string|null: false, index: true|
|email|string|null: false, unique: true|
|password|string|null: false|

### association

- has_many :gropus_users
- has_many :groups, through: :gropus_users
- has_many :Messages

## messagesテーブル

|column|type|options|
|------|----|-------|
|text|string||
|image|string||
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### association

- belongs_to :user
- belongs_to :group

## groupsテーブル

|column|type|options|
|------|----|-------|
|name|string|null: false|

### association

- has_many :groups_users
- has_many :users, through: :groups_users
- has_many :messages

## gropus_usersテーブル

|column|type|options|
|------|----|-------|
|group_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|

### association

- belongs_to :user
- belongs_to :group