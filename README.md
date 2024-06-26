api_final

Описание:
api final - это REST API для блог-платформы Yatube. Позволяет просматривать и отправлять посты, просматривать группы, подписываться на авторов.

Как запустить проект:
Клонировать репозиторий и перейти в него в командной строке:

git clone git@github.com:Bant0n/api_final_yatube.git
cd api_final_yatube
Cоздать и активировать виртуальное окружение:

python -m venv venv
source venv/Scripts/activate 
Установить зависимости из файла requirements.txt:

python -m pip install --upgrade pip
pip install -r requirements.txt
Выполнить миграции:

python manage.py migrate
Запустить проект:

python manage.py runserver
Примеры запросов:
Запрос JWT токена с использованием логина и пароля пользователя Admin:
  [POST].../api/v1/jwt/create/
  {
    "username": "Admin",
    "password": "12345..."
}
Ответ:
{"refresh": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoicmVmcmVzaCIsImV4cCI6MTY1MjA5NTYwNywianRpIjoiMDBmMGI0MG.sE5Bd3vrnQLIAL5GxxFg36tPoYyB9I5MQBE_iGshpK4",
    "access": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNjUyMDk1NjA3LCJqdGkiOiI0YmIxN2MzODcwNGU0YzQ0OWQ4Nzg4NzA4ODcyZTliMCIsInVzZXJfaWQiOjF9"
}
Запрос с использованием токена пользователя Admin для публикации поста:
    [POST].../api/v1/posts/
    {
    "text": "Любой текст ...",
    "group": 1   
    }
Ответ:
{
    "id": 2,
    "author": "Admin",
    "text": "Любой текст ...",
    "pub_date": "2023-09-15T15:14:51.119243Z"
    "image": null,
    "group": 1,
}
Запрос для просмотра групп анонимным пользователем:
    [GET].../api/v1/groups/
Пример ответа:
[
  {
    "id": 1,
    "title": "Пост с группой",
    "slug": "post_with_group",
    "description": "Пост с группой"
  }
]
Подробная документация в формате ReDoc доступна по адресу .../redoc/