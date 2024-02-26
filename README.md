# recipe-app-api

Recipe API project.

## Command Order

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
