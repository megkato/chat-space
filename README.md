## userテーブル

|Column|Type|Options|
|------|----|-------|
|email|string|null: false, unique: true|
|password|string|null: false|
|name|string|index: true, null: false, unique:true|

### Association
- has_many :messages
- has_many :groups_users
- has_many :groups, through: groups_users

## groupテーブル

|Column|Type|Options|
|------|----|-------|
|group_name|text|index: true, null: false|
|user_id|integer|null: false, foreign_key: true|

### Association
- has_many :groups_users|
- has_many :messages
- has_many :users, through: groups_users|

## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|body|text|null: false|
|image|string|
|group_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user