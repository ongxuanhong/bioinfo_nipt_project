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