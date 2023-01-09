# Foodgram - Продуктовый помощник

Foodgram это ресурс для публикации рецептов.  
Пользователи могут создавать свои рецепты, читать рецепты других пользователей, подписываться на интересных авторов, добавлять лучшие рецепты в избранное, а также создавать список покупок и загружать его в pdf формате

## Инструкция по установке проекта локально. БД - SQLite3

* Склонировать репозиторий на локальную машину:
```
git clone https://github.com/MaidariTs/foodgram-project-react.git
cd foodgram-project-react
```

* Cоздать и активировать виртуальное окружение:

```
python -m venv venv

``` for Windows
. venv/Scripts/activate

``` for Linux
. venv/bin/activate
```

* Установить зависимости:

```
cd backend/
pip install -r requirements.txt
```

* Применить миграции:
```
python manage.py makemigrations
```
```
python manage.py migrate
```
* Загрузить ингредиенты:
```
python manage.py load_ingrs
```
* Загрузить теги:
```
python manage.py load_tags
```
* Создать администратора:
```
python manage.py createsuperuser
```
* Собрать статику:
```
python manage.py collectstatic --noinput
```
* Запустить сервер:
```
python manage.py runserver
```

## Backend by
[Цыденов Майдари](https://github.com/MaidariTs)
