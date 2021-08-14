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
```
