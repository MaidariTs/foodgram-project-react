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
Проект доступен по адресу 


## Инструкция по установке проекта на сервер

* Форкнуть репозиторий к себе на GitHub https://github.com/MaidariTs/foodgram-project-react.git

* Склонировать репозиторий:

```
git clone https://github.com/<YOUR_GITHUB_NICKNAME>/foodgram-project-react.git
cd foodgram-project-react
```

* Репозиторий **foodgram-project-react.git >> Settings >> Secrets and variables > Actions**
* Указать следующие переменные:

**.env**
- ```SECRET_KEY``` - секретный ключ от django
- ```ALLOWED_HOSTS``` - список разрешенных адресов (default='*')

**DOCKER**
- ```DOCKER_USERNAME``` - никнейм в DockerHub
- ```DOCKER_PASSWORD``` - пароль от DockerHub

**SERVER**
- ```HOST``` - публичный IPv4 сервера
- ```USER``` - никнейм пользователя
- ```SSH_KEY``` - приватный ssh ключ (cat ~/.ssh/id_rsa)
- ```PASSPHRASE``` - кодовая фраза для ssh-ключа

**DB**
- ```DB_ENGINE``` - django.db.backends.postgresql
- ```DB_NAME``` - postgres
- ```POSTGRES_USER``` - postgres
- ```POSTGRES_PASSWORD``` - postgres
- ```DB_HOST``` - db
- ```DB_PORT``` - 5432

**TELEGRAM**
- ```TELEGRAM_TO``` - id от телеграмм аккаунта
- ```TELEGRAM_TOKEN``` - токен бота

* Перейти в папку /infra
```
cd infra/
```

* В строке server_name заменить IPv4 на свой

* Передать файлы docker-compose.yml и nginx.conf на свой сервер
```
scp docker-compose.yml <username>@<host>:/home/<username>/docker-compose.yml
scp nginx.conf <username>@<host>:/home/<username>/nginx.conf
```

* Зайти на сервер
```
ssh username@server_address
```

* Обновить установленные пакеты:
```
sudo apt update
sudo apt upgrade -y
```

* Установить Docker и Docker-compose:
```
sudo apt install docker.io
```
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
```
sudo chmod +x /usr/local/bin/docker-compose
```

* Выйти из сервера
```
exit
```

* Запушить изменения на GitHub
```
git add .
git commit -m 'start'
git push
```

## Всё. При пуше изменений на GitHub запустится workflow, который автоматически протестирует, загрузит на DockerHub образы и задеплоит на сервер

## Готово! Проект доступен по ссылке:
```
http://51.250.9.252/recipes/
```

## Backend by
[Цыденов Майдари](https://github.com/MaidariTs)
