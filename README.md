# Foodgram - Продуктовый помощник

«Foodgram»: сайт, на котором пользователи могут публиковать рецепты, добавлять чужие рецепты в избранное и подписываться на публикации других авторов. Сервис «Список покупок» позволит пользователям создавать список продуктов, которые нужно купить для приготовления выбранных блюд и загружать список в pdf формате.

## Инструкция по установке проекта локально

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

* Обновить pip
```
python -m pip install --upgrade pip
```

* В директории 'infra/' необходимо создать файл '.env' и заполнить его:
cd ..
cd infra/
```
ALLOWED_HOSTS='*'
SECRET_KEY=<Секретный ключ Django> (в кавычках)
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
```

* Запустить файл docker-copmose.yml
```
docker-compose up -d --build
```
* Применить миграции:
```
docker-compose exec backend python manage.py migrate
```
* Загрузить ингредиенты из файла в БД:
```
docker-compose exec backend python manage.py load_ingredients
```
* Загрузить тэги из файла в БД:
```
docker-compose exec backend python manage.py load_tags
```
* Создайть суперюзера:
```
docker-compose exec backend python manage.py createsuperuser
```
* Собрать статику:
```
docker-compose exec backend python manage.py collectstatic --noinput
```


scp docker-compose.yml <username>@<host>:/home/<username>/docker-compose.yml

scp nginx.conf <username>@<host>:/home/<username>/nginx.conf

scp docker-compose.yml maidaritsydenov@51.250.9.252:/home/maidaritsydenov/docker-compose.yml
scp nginx.conf maidaritsydenov@51.250.9.252:/home/maidaritsydenov/nginx.conf


docker-compose exec backend python manage.py collectstatic --no-input




## Готово! Документация к проекту по ссылке:
```
http://127.0.0.1/api/docs/
```

## Backend by
[Цыденов Майдари](https://github.com/MaidariTs)
