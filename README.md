
## アプリケーション名
Rails Error Sharing Hub

## アプリケーション概要
このアプリケーションは、エラーの投稿・管理、ログイン機能、コメント機能を提供し、ユーザー間でのエラー解決や情報共有を促進します。

## URL
デプロイが完了次第記載いたします。

## 利用方法
1. アプリケーションにアクセスします。
2. ログインページで、既存のアカウントでログインするか、新規アカウントを作成します。
3. ログイン後、投稿機能を使用してエラーを投稿します。
4. 一覧機能で投稿されたエラーを閲覧します。
5. エラーの詳細を確認するには、詳細機能を使用します。
6. 自身の投稿を編集・削除する場合は、編集機能および削除機能を使用します。
7. 検索機能で特定のエラーを絞り込んで検索します。
8. コメント機能を使用して他のユーザーとコミュニケーションを行います。

## アプリケーションを作成した背景
このアプリケーションは、ソフトウェア開発におけるエラー管理の課題に対処するために開発されました。開発者は常に、発生したエラーの詳細を共有し、解決策を迅速かつ効果的に見つける必要があります。このニーズから、エラー共有ハブを作成し、開発コミュニティの効率的なコラボレーションを実現することを目指しました。

## 洗い出した要件
[要件定義スプレッドシート](https://docs.google.com/spreadsheets/d/1IKEcL8WXkHtOJnz0NiBOBo-g9oODD3yOaDYI9j2aE5c/edit#gid=982722306)

## データベース設計
[ER図](https://gyazo.com/f302e7b5f978c953d08cd9c59d9741b9)
[![Image from Gyazo](https://i.gyazo.com/f302e7b5f978c953d08cd9c59d9741b9.png)](https://gyazo.com/f302e7b5f978c953d08cd9c59d9741b9)

# テーブル設計詳細

## users テーブル

| Column               | Type   | Options     |
| ------------------   | ------ | ----------- |
| nickname             | string | null: false |
| email                | string | null: false, unique: true |
| encrypted_password   | string | null: false |
| last_name            | string | null: false |
| first_name           | string | null: false |
| last_name_kana       | string | null: false |
| first_name_kana      | string | null: false |

### Association

- has_many :posts
- has_many :comments

## posts テーブル

|     Column                 | Type    | Options     |
|     ------                 | ------  | ----------- |
| title                      | string  | null: false |
| content                    | text    | null: false |
| category_id                | integer | null: false |   
| solution                   | string  | null: false | 
| user                       | references | null: false, foreign_key: true |

### Association

- has_one : user
- belongs_to :user
- has_many :comments

## comments テーブル

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| item    | references | null: false, foreign_key: true |
| user    | references | null: false, foreign_key: true |

### Association

- belongs_to :post
- belongs_to :user


## 開発環境
- Ruby
- Ruby on Rails
- MySQL
- Github
- Visual Studio Code
