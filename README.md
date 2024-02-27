# recipe-app-api

Recipe API project.

## Command Order

#### Build docker container after docker-compose file configured

```
docker compose build
```

#### Create Django project

```
docker compose up run --rm app sh -c "django-admin startproject app ."
```

#### Run project with docker compose

```
docker compose up
```

#### Run unitest

```
docker compose run --rm app sh -c "python manage.py test"
```

#### Create core app

```
docker compose run --rm app sh -c "python manage.py startapp core"
```

#### Test custom command

```
docker compose run --rm app sh -c "python manage.py wait_for_db"
```

#### User model migrations

```
docker compose run --rm app sh -c "python manage.py makemigrations"
```

#### Apply migrations and db test

```
docker compose run --rm app sh -c "python manage.py wait_for_db && python manage.py migrate"
# if you have InconsistentMigrationHistory error
docker compose down
docker volume ls
docker volume rm recipe-app-api_dev-db-data
docker compose run --rm app sh -c "python manage.py wait_for_db && python manage.py migrate"
```

#### Test user model

```
docker compose up
docker compose run --rm app sh -c "python manage.py createsuperuser"
# input super user with Email and Password
# go to localhost:8000/admin try to login with above info

```

#### Build user api

```
docker compose rum --rm app sh -c "python manage.py startapp user"
```

Then remove `migrations`, `admin.py`, `models.py`, `tests.py`.
Create `tests` folder with `__init__.py`
Add 'user' inside `app>settings.py>INSTALLED_APPS`.
