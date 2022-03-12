## Учебный проект 16 спринта факультета бэкенд-разработки

![example workflow](https://github.com/Shchegolyaev/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

**Проект YaMDb собирает отзывы пользователей на произведения.**

**Произведения делятся на категории: Книги, Фильмы, Музыка.**

## Стек:
- Python
- Django
- Docker
- Nginx
- И так далее (более подробно можно ознакомиться здесь `api_yamdb/requirements.txt`)


## Руководство по установке Docker
Информация по установке Docker  [здесь](https://docs.docker.com/engine/install/)

## Руководство по запуску проекта:

Клонировать репозиторий:

```bash
git clone https://github.com/Tar8117/infra_sp2.git
```
Либо, если используете доступ к Github через SSH:
```bash
git clone git@github.com:Tar8117/infra_sp2.git
```
Перейти в склонированный репозиторий:
```bash
cd api_yamdb/
```

Cоздать и активировать виртуальное окружение:

```bash
python3 -m venv env
```

```bash
source env/bin/activate
```

```bash
python3 -m pip install --upgrade pip
```

Установить зависимости из файла requirements.txt:

```bash
pip install -r requirements.txt
```

Запустить приложение в контейнерах:

*из директории `infra/`*
```bash
docker-compose up -d --build
```

Выполнить миграции:

*из директории `infra/`*
```bash
docker-compose exec web python manage.py migrate
```

Создать суперпользователя:

*из директории `infra/`*
```bash
docker-compose exec web python manage.py createsuperuser
```

Собрать статику:

*из директории `infra/`*
```bash
docker-compose exec web python manage.py collectstatic --no-input
```

Остановить приложение в контейнерах:

*из директории `infra/`*
```bash
docker-compose down -v
```
Запуск `pytest`:

*при запущенном виртуальном окружении*
```bash
cd infra_sp2 && pytest
```
### Создайте файл .env со значениями:
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=oliver
DB_HOST=db
DB_PORT=5432

### Документация API с примерами:

```json
/redoc/
```

### описание команды для заполнения базы данными
```bash
cd api_yamdb && python manage.py loaddata ../infra/fixtures.json
```
