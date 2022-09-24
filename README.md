## アプリケーション名　　
「protopapace」  

## アプリケーションの概要  
 アプリ開発をしているユーザーが、プロトタイプについてフィードバックを得られるサービスです。  
 ※プロトタイプとはアプリの試作品のことです。
  
## 利用方法  
 新規ユーザー登録をします  
   
## データベース設計  
  
### usersテーブル　　

| Culum              | Type   | Option                    |
| ------------------ | ------ | ------------------------- |
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false               |
| name               | string | null: false               |
| profile            | text   | null: false               |
| occupation         | text   | null: false               |
| position           | text   | null: false               | 

#### Association  

- has_many :prototypes
- has_many :comments


### prototypesテーブル  

| Culum      | Type       | Option                         |
| ---------- | ---------- | ------------------------------ |
| title      | string     | null: false                    |
| catch_copy | text       | null: false                    |
| concept    | text       | null: false                    |
| user       | references | null: false, foreign_key: true |

#### Association  

- has_many :comments
- belongs_to :user


### commentsテーブル  

| Culum     | Type       | Option                         |  
| --------- | ---------- | ------------------------------ |
| content   | text       | null: false                    |
| prototype | references | null: false, foreign_key: true |
| user      | references | null: false, foreign_key: true |

#### Association  

- belongs_to :user
- belongs_to :prototype

