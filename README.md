# SocialBloggingAPI

### Описание
Проект социальная сети которая позволяет публиковать посты и оставлять под ними
комментарии. Так же можно подписываться на интересных авторов и группы.
У каждого поста есть список тем к которым он относится и для каждой темы
есть отдельная группа, в которой находятся связанные посты.

### Стек
* Django Rest Framework
* SQLite
* Git
* Postman

### Как запустить проект
* Клонировать репозиторий:
```bash
git clone git@github.com:Valievx/SocialBloggingAPI.git
```

* Создать и активировать виртуальную среду, установить зависимости
```bash
python -m venv venv
Win: source venv/Scripts/activate 
Unix: source venv/bin/activate
pip install -r requirements.txt
```

* Перейти в папку проекта:

```bash
cd yatube_api
```

* Выполнить миграции:

```bash
python manage.py migrate
```

* Создать администратора:

```bash
python manage.py createsuperuser
```

* Запустить проект:

```bash
python manage.py runserver
```

### Документация находится в файле `yatube_api/static/redoc.yaml`

### Примеры запросов к API

#### Получение публикаций с 11 по 20 (GET):

```/api/v1/posts/?offset=10&limit=10```

Формат ответа:

```JSON
{
  "count": 12,
  "next": null,
  "previous": "http://127.0.0.1:8000/api/v1/posts/?limit=10",
  "results": [
    {
      "id": 11,
      "author": "valiev",
      "text": "Some text",
      "pub_date": "2023-04-03T12:05:16.012992Z",
      "image": null,
      "group": null
    },
    {
      "id": 12,
      "author": "valiev",
      "text": "Some text",
      "pub_date": "2023-04-03T12:05:16.639890Z",
      "image": null,
      "group": null
    }
  ]
}
```

#### Запрос для создания публикации (POST):

```/api/v1/posts/```

Тело запроса:
```JSON
{ "text": "Some text" }
```
Формат ответа:

```JSON
{
  "id": 1,
  "author": "valiev",
  "text": "Some text",
  "pub_date": "2023-04-03T12:02:24.017693Z",
  "image": null,
  "group": null
}
```

#### Подписаться на пользователя (POST):
```/api/v1/follow/```

Тело запроса:
```JSON
{ "following": "username" }
```

Формат ответа:
```JSON
{ 
  "user": "your_username",  
  "following": "username"
}
```

## **Остальные запросы :**
* Получение публикаций - http://127.0.0.1:8000/api/v1/posts/ [GET]
* Создание публикации - http://127.0.0.1:8000/api/v1/posts/ [POST]
* Получение публикации - http://127.0.0.1:8000/api/v1/posts/{id}/ [GET]
* Обновление публикации - http://127.0.0.1:8000/api/v1/posts/{id}/ [PUT]
* Частичное обновление публикации - http://127.0.0.1:8000/api/v1/posts/{id}/ [PATCH]
* Удаление публикации - http://127.0.0.1:8000/api/v1/posts/{id}/ [DEL]
* Получение комментариев - http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/ [GET]
* Добавление комментария - http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/ [POST]
* Получение комментария - http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/{id}/ [GET]
* Обновление комментария - http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/{id}/ [PUT]
* Частичное обновление комментария - http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/{id}/ [PATCH]
* Удаление комментария - http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/{id}/ [DEl]
* Список сообществ - http://127.0.0.1:8000/api/v1/groups/ [GET]
* Информация о сообществе - http://127.0.0.1:8000/api/v1/groups/{id}/ [GET]
* Подписки - http://127.0.0.1:8000/api/v1/follow/ [GET]
* Подписка - http://127.0.0.1:8000/api/v1/follow/ [POST]
* Получить JWT-токен - http://127.0.0.1:8000/api/v1/jwt/create/ [POST]
* Обновить JWT-токен - http://127.0.0.1:8000/api/v1/jwt/refresh/ [POST]
* Проверить JWT-токен - http://127.0.0.1:8000/api/v1/jwt/verify/ [POST]
