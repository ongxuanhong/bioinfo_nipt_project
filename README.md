# bioinfo_nipt_project

```bash
python -m pip install Django
django-admin startproject nipt_backend
cd nipt_backend
python manage.py runserver
```

## How to export mermaid graph
```bash
docker run --rm -v $(pwd):/data minlag/mermaid-cli \
    -i mermaid/nipt-workflow.mermaid \
    -o mermaid/nipt-workflow.svg
```

## Working with Django
```bash
pip3 install pipenv
pipenv install Django
pipenv shell
pipenv lock

django-admin startproject niptapp
python3 manage.py migrate
python3 manage.py runserver

docker build .
docker-compose build
docker-compose up -d


STATIC_URL = '/static/'
STATIC_ROOT = BASE_DIR / 'static'
STATICFILES_DIRS = [
    'niptapp/static'
]
python3 manage.py collectstatic


python3 manage.py startapp accounts
python3 manage.py makemigrations
python3 manage.py migrate
python3 manage.py createsuperuser


python3 manage.py startapp workflows
python3 manage.py makemigrations
python3 manage.py migrate

urlpartterns
templates
```