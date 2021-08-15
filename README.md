# git setting

```
echo "# Template_Django_on_Docker" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/miyamoto-kentaro/Template_Django_on_Docker.git
git push -u origin main
```

# django setup

```
create django dir as "app"
$ cd app
/app$ python3 -m venv .venv
(.venv)/app$ source .venv/bin/activate
(.venv)/app$ pip install update pip
(.venv)/app$ pip install -U pip
(.venv)/app$ pip install django
(.venv)/app$ python
=> version: 3.8.10
(.venv)/app$ django-admin startproject config .
config is django application folder. it's able to changed.
(.venv)/app$ python manage.py migrate
(.venv)/app$ python manage.py createsuperuser
(.venv)/app$ python manage.py runserver
(.venv)/app$
(.venv)/app$
(.venv)/app$
(.venv)/app$
```

# docker setup

```
create docker file and docker compose.yaml

$ docker-compose build
$ docker-compose up -d
$ connect localhost:8000
if you want to see log
$ docker-compose logs -f

$ docker-compose up -d --build

check the create volum
$ docker volume ls
[O]:
DRIVER    VOLUME NAME
local     template_django_on_docker_postgres_data
$ docker volume inspect template_django_on_docker_postgres_data

create sh file into app
$ chmod +x app/entrypoint.sh

$ docker-compose -f docker-compose.prod.yaml up -d --build
```

## database setup with django

```
$ docker-compose exec web python manage.py migrate --noinput
$ docker-compose exec db psql --username=hello_django --dbname=hello_django_dev

killing container with volumes
$ docker-compose down -v

finaly up
$ docker-compose -f docker-compose.prod.yaml down -v
$ docker-compose -f docker-compose.prod.yaml up -d --build
$ docker-compose -f docker-compose.prod.yaml exec web python manage.py migrate --noinput
$ docker-compose -f docker-compose.prod.yaml exec web python manage.py collectstatic --no-input --clear

$ docker-compose logs -f
```
