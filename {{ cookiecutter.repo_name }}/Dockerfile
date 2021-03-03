FROM python:3.8-slim

ENV PIPENV_SKIP_LOCK=1

RUN apt update && apt install -y \
    sudo 

RUN pip3 install pipenv

ARG USERNAME=dev
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN adduser ${USERNAME} --gecos "" --disabled-password &&\
    echo ${USERNAME} ALL=\(ALL\) NOPASSWD:ALL > /etc/sudoers.d/${USERNAME} &&\
    chmod 0440 /etc/sudoers.d/${USERNAME}

USER ${USERNAME}

RUN echo 'export PS1="🐳 \[\033[1;36m\][\u@docker] \[\033[1;34m\]\W\[\033[0;35m\] # \[\033[0m\]"' >> /home/${USERNAME}/.bashrc

WORKDIR /app
RUN sudo chown -R ${USERNAME} .

COPY --chown=${USERNAME} Pipfile setup.py ./
COPY --chown=${USERNAME} src/__init__.py src/

RUN pipenv install

COPY --chown=${USERNAME} . .

CMD ["pipenv", "run", "python", "main.py"]

