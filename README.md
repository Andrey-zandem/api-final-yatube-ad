# Social Media API

API для социальной сети с постами, комментариями, группами и подписками.

# Установка и запуск

Клонировать репозиторий и перейти в него в командной строке:

git clone https://github.com/your-username/kittygram.git
cd kittygram


Cоздать и активировать виртуальное окружение:

python3 -m venv env
source venv/bin/activate  # Для Linux/macOS

venv\Scripts\activate  # Для Windows

Установить зависимости из файла requirements.txt:

python3 -m pip install --upgrade pip
pip install -r requirements.txt

Выполнить миграции:

python3 manage.py migrate

Запустить проект:

python3 manage.py runserver

# Аутентификация
Получение токена:

POST /api/token/
{
    "username": "your_username",
    "password": "your_password"
}

Ответ:
json
{
    "access": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9...",
    "refresh": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9..."
}


# Примеры запросов к API

# Посты

GET /api/posts/ — получить список всех постов

POST /api/posts/— создать новый пост
json
{
    "text": "Текст поста",
    "image": "base64_encoded_image"  // опционально
}


# Комментарии

GET /api/posts/{post_id}/comments/ — получить комментарии к посту

POST /api/posts/{post_id}/comments/ — добавить комментарий
json
{
    "text": "Текст комментария"
}


# Группы

GET /api/groups/ — получить список всех групп

# Подписки

GET /api/follow/ — получить список подписок текущего пользователя

POST /api/follow/ — подписаться на пользователя
json
{
    "following": "username"
}


GET /api/follow/?search=username — поиск по подпискам

# Права доступа

- Анонимные пользователи: только чтение постов и групп
- Авторизованные пользователи: создание постов, комментариев, подписок
- Авторы: редактирование и удаление своих постов и комментариев


