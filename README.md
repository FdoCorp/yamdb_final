![example workflow](https://github.com/FdoCorp/yamdb_final/actions/workflows/main.yml/badge.svg)
# Api_yamdb

REST API проект для сервиса YaMDb — сбор отзывов о фильмах, книгах или музыке.

## Описание

Проект YaMDb собирает отзывы пользователей на произведения.
Произведения делятся на категории: «Книги», «Фильмы», «Музыка».
Список категорий  может быть расширен (например, можно добавить категорию «Изобразительное искусство»)

## Технологии и их версии
В проекте использовались такие технологии, как:
- requests
- Django
- djangorestframework
- PyJWT
- pytest
- pytest-django
- pytest-pythonpath
- djangorestframework-simplejwt
- django-filter


## Как запустить проект пользователям системы Windows
Клонировать репозиторий и переходим в него
```bash
git clone git@github.com:FdoCorp/infra_sp2.git
cd infra_sp2
cd api_yamdb
```

Перейти в папку с файлов docker-compose.yaml:
```bash
cd infra
```

Поднять контейнеры (infra_db_1, infra_wed_1, infra_nginx_1):
```bash
docker-compose up -d --build
```

Выполнить миграции командой
```bash
python manage.py migrate
```
docker-compose exec web python manage.py makemigrations reviews
```
```bash
docker-compose exec web python manage.py migrate
```

Создать суперпользователя:
```bash
docker-compose exec web python manage.py createsuperuser
```

Собирать статику:
```bash
docker-compose exec web python manage.py collectstatic --no-input
```

Создать дамп базы данных (нет в текущем репозитории):
```bash
docker-compose exec web python manage.py dumpdata > dumpPostrgeSQL.json
```

Останавливать контейнеры:
```bash
docker-compose down -v
```

### Шаблон наполнения .env (не включен в текущий репозиторий) расположенный по пути infra/.env
```
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
```

### Документация API YaMDb
Документация доступна по эндпойнту: http://localhost/redoc/


## Автор
+ [Дмитрий Емельянов](https://github.com/FdoCorp)
