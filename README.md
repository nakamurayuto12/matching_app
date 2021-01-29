# DB 設計

## user table

| Column             | Type                | Options                       |
|--------------------|---------------------|-------------------------------|
| email              | string              | unique: true, null: false     |
| encrypted_password | string              | null: false                   |
| birthday           | date                | null: false                   |
| surname            | string              | null: false                   |
| name               | string              | null: false                   |
| surname_furigana   | string              | null: false                   |
| name_furigana      | string              | null: false                   |
| nickname           | string              | null: false                   |
| sex                | string              | null: false                   |


### Association

* has_many :chat_room_message
* has_many :user_chat_room
* has_many :TIME_LINE

## user_chat_room table

| Column              | Type           | Options           |
|---------------------|----------------|-------------------|
| chat_room           | references     | foreign_key: true |
| user                | references     | foreign_key: true |


### Association

- belongs_to :user
- belongs_to :chat_room

 ## chat_room table

| Column              | Type       | Options           |
|---------------------|------------|-------------------|
| user                | references | foreign_key: true |

### Association

- belongs_to :chat_room_message
- belongs_to :user_chat_room

## chat_room_message table

| Column              | Type       | Options           |
|---------------------|------------|-------------------|
| message             | text       | null: false       |
| user                | references | foreign_key: true |
| chat_room           | references | foreign_key: true |


### Association

belongs_to :chat_room
belongs_to :user

## TIME_LINE table

| Column              | Type       | Options           |
|---------------------|------------|-------------------|
| text                | text       | null: false       |
| user                | references | foreign_key: true |

### Association

belongs_to :user
has_many :comment

## comment table

| Column              | Type       | Options           |
|---------------------|------------|-------------------|
| comment             | text       | null: false       |
| user                | references | foreign_key: true |

### Association

belongs_to :TIME_LINE
