## ![](https://github.com/anign/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

### [YamDB ReDOC](http://158.160.30.65/redoc/)
### [YamDB API](http://158.160.30.65/api/v1/)
### [YamDB admin panel](http://158.160.30.65/admin/)

# Запуск docker-compose
```
Это проектное задание модуля CI и CD, часть курса "Python-developer"
от Яндекс-практикум
```
## Автор
```
Антон Игнатьев
```
## Использованные технологии:
```
Python
```
```
Django
```
```
Docker
```
## ENV doc
```
Example of .env
```
DB_ENGINE= указываем, что работаем с postgresql
```
DB_NAME= имя базы данных
```
POSTGRES_USER= логин для подключения к базе данных
```
POSTGRES_PASSWORD= пароль для подключения к БД (установите свой)
```
DB_HOST= название сервиса (контейнера)
```
DB_PORT= порт для подключения к БД
```
## Как запустить проект:
```
Все описанное ниже относится к ОС Linux.
```
Клонируем репозиторий и переходим в него:
```bash
cd api_yamdb
```
Создаем и активируем виртуальное окружение:
```bash
python3 -m venv venv
source /venv/bin/activate (source /venv/Scripts/activate - для Windows)
python -m pip install --upgrade pip
```

Ставим зависимости из requirements.txt:
```bash
pip install -r requirements.txt
```

Переходим в папку с файлом docker-compose.yaml:
```bash
cd infra
```

Поднимаем контейнеры (infra_db_1, infra_web_1, infra_nginx_1):
```bash
docker-compose up -d --build
```

Выполняем миграции:
```bash
docker-compose exec web python manage.py makemigrations
```
```bash
docker-compose exec web python manage.py migrate
```

Создаем суперпользователя:
```bash
docker-compose exec web python manage.py createsuperuser
```

Загружаем данные из фикстуры:
```bash
docker-compose exec web python manage.py loaddata fixtures.json
```

Собираем статику:
```bash
docker-compose exec web python manage.py collectstatic --no-input
```
Останавливаем контейнеры:
```
docker-compose down -v
```
