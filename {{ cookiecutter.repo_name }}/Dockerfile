FROM python:3.8-slim

RUN echo 'export PS1="🐳 \[\033[1;36m\][\u@docker] \[\033[1;34m\]\W\[\033[0;35m\] # \[\033[0m\]"' >> /root/.bashrc

ENV PIPENV_VENV_IN_PROJECT=1
ENV PIPENV_SKIP_LOCK=1

RUN apt update && apt upgrade -y && \
    apt install -y pipenv python3-pip

RUN pip3 install virtualenv

WORKDIR /app

COPY Pipfile setup.py ./
COPY src/__init__.py src/

RUN pipenv install --skip-lock

COPY . .

CMD ["pipenv", "run", "python", "main.py"]

