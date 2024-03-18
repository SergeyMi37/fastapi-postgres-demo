# FastAPI demo with Postgres using SQLAlchemy

This is a simplest demo of FastAPI on Postgres using SQLAlchemy

## Using

Build docker compose environment

```shell
docker-compose build
```

Start in development mode

```shell
docker-compose up app
```

Access docs page: http://localhost:8000/docs


## Создание виртуального окружения для проекта
### Для Windows
```cmd
python -m venv env
source env/Scripts/activate
```

### Для Linux
```bash
python3 -m venv env
source env/bin/activate
```

# Как запустить бэкэнд локально

## Копировать в файл .env переменную окружения DATABASE_URL из файла env.sample

## Установить СУБД PostgreSql
создать базу данных testdemo программой pgAdmin
или из терминала
```bash
sudo -u postgres psql
postgres-# CREATE DATABASE testdemo;
postgres-# \conninfo
You are connected to database "postgres" as user "postgres" via socket in "/var/run/postgresql" at port "5432".
postgres-# \?
postgres-# alter user postgres with password 'postgres';
postgres-# \q
```

## Установки зависимости:  
```bash
pip install -r requirements.txt
```

## Создать .env файл на основе env.sample


## Запустить миграции
```bash
alembic upgrade head
```

## Необходимо перейти в каталог бэкенд:  
```bash
uvicorn app.main:app --workers 1 --host 0.0.0.0 --port 8000 --env-file .env
```
или
```
python -m uvicorn app.main:app --workers 1 --host 0.0.0.0 --port 8000 --env-file .env
```
