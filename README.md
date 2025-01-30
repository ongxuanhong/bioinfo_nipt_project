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

## Working with Airflow
```bash
curl -LfO 'https://airflow.apache.org/docs/apache-airflow/2.3.3/docker-compose.yaml'
mkdir airflow && cd airflow
mkdir -p ./dags ./logs ./plugins
echo -e "AIRFLOW_UID=$(id -u)" > .env

docker-compose up airflow-init
docker-compose up -d
http://localhost:8080/
airflow, airflow

docker-compose run airflow-worker airflow info

ENDPOINT_URL="http://localhost:8080"
DAG_ID="example_bash_operator"
DAG_RUN_ID="manual_trigger_1"

# Checking REST API
curl -X GET  \
    --user "airflow:airflow" \
    "${ENDPOINT_URL}/api/v1/pools"

# Get list tasks of DAG
curl -X GET  \
    --user "airflow:airflow" \
    "${ENDPOINT_URL}/api/v1/dags/${DAG_ID}/tasks"

# Submit task of DAG
curl -X POST \
  --user "airflow:airflow" \
  -H "Content-Type: application/json" \
  -d '{
    "dag_run_id": "manual_trigger_1",
    "conf": {}
  }' \
  "${ENDPOINT_URL}/api/v1/dags/${DAG_ID}/dagRuns"

# Get list runs of DAG
curl -X GET \
  --user "airflow:airflow" \
  "${ENDPOINT_URL}/api/v1/dags/${DAG_ID}/dagRuns"

# Get task instance of DAG
curl -X GET \
  --user "airflow:airflow" \
  "${ENDPOINT_URL}/api/v1/dags/${DAG_ID}/dagRuns/${DAG_RUN_ID}/taskInstances"  

```