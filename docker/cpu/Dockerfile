# sandbox的に使うので軽量イメージを使う
FROM python:3.11.8-bullseye

ENV TZ=Asia/Tokyo
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

ENV PYTHONPATH "${PYTHONPATH}:/workspace"
WORKDIR /workspace

ENV POETRY_HOME=/opt/poetry
RUN curl -sSL https://install.python-poetry.org/ | python3 - --version 1.8.2 && \
    cd /usr/bin && \
    ln -s /opt/poetry/bin/poetry && \
    poetry config virtualenvs.create false

COPY ./pyproject.toml ./poetry.lock* ./
RUN poetry install
