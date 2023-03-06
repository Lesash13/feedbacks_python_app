FROM python:3.9-slim

WORKDIR /app

COPY api_yamdb/requirements.txt .

RUN pip3 install --upgrade pip --no-cache-dir

RUN pip3 install -r requirements.txt --no-cache-dir

COPY api_yamdb .

COPY infra/fixtures.json fixtures.json

RUN python manage.py collectstatic --no-input

CMD ["gunicorn", "api_yamdb.wsgi:application", "--bind", "0:8000" ]