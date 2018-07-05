# graphene-flask-example

Example of an API [GraphQL](http://graphql.org/) using [Graphene](http://docs.graphene-python.org/en/latest/quickstart/), [Flask GraphQL](https:/ /github.com/graphql-python/flask-graphql) and [Graphene-SQLAlchemy](http://docs.graphene-python.org/projects/sqlalchemy/en/latest/).

## Installation

### Virtualenv

[Installation](https://virtualenv.pypa.io/en/stable/installation/)

```
  virtualenv --python python3 venv
  source venv/bin/activate
  pip install -U pip
  pip install -r requirements-dev.txt
```

### Tox

[Installation](https://tox.readthedocs.io/en/latest/)

```
tox
```

### Docker-Compose

[Installation](https://docs.docker.com/compose/install/)

```
docker-compose up #create and run web and db containers
docker-compose run --service-ports --name user_api_flask_web web --rm #allow application server to stop on breakpoints
docker-compose exec web bash #open the web container terminal
docker-compose exec db mysql #open mysql CLI in db container
```

## Setting the local environment

Create a local .env file based on the .env.sample file.

## Run from local server

```
  python run.py #run local server on port 3000
```

## Database versioning

The application uses [Flask-Migrate](https://github.com/miguelgrinberg/Flask-Migrate) to do database versioning.

First create the database for the development and test environments.

```
mysql -e "create database user_db;"
mysql -e "create database user_db_test;"
```

Right away:

```
python manage.py db migrate #create migration if there is a change in the database schema
python manage.py db upgrade #run database migrations
```

### Routes

```

GET /api/healthcheck

GET /api/graphql

```

## Execution of unit tests

```
pytest
```

## Linter

```
flake8 tests user_api
```