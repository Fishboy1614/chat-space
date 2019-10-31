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

# chat-space DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|username|string|null: false|
|chat_id|integer|null: false, foreign_keys: true|
### Association
- has_many :users_chats
- has_many :chats, through: :users_chats
- has_many :messages

## chatsテーブル
|Column|Type|Options|
|------|----|-------|
|chatname|string|null: false|
|user_id|integer|null: false, foreign_keys: true|
### Association
- has_many :users_chats
- has_many :users, through: :users_chats
- has_many :messages

## users_chatsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|chat_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :chat

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|text|text|null: false|
|image|text||
|user_id|integer|null: false, foreign_key: true|
|chat_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :chat