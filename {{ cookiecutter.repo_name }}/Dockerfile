FROM python:3.8-slim

RUN apt update && apt upgrade -y && \
    apt install -y pipenv

WORKDIR /app

COPY Pipfile setup.py ./
COPY src/__init__.py src/

RUN pipenv install --skip-lock

COPY . .

CMD ["pipenv", "run", "python", "main.py"]

