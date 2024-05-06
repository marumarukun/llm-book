# sandbox的に使うのでruntimeイメージを使う
FROM nvidia/cuda:12.4.1-runtime-ubuntu22.04

ENV TZ=Asia/Tokyo
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y curl python3-dev git && \
    apt-get upgrade -y && \
    apt-get clean

ENV PYTHONPATH "${PYTHONPATH}:/workspace"
WORKDIR /workspace

ENV POETRY_HOME=/opt/poetry
RUN curl -sSL https://install.python-poetry.org/ | python3 - --version 1.8.2 && \
    cd /usr/bin && \
    ln -s /opt/poetry/bin/poetry && \
    poetry config virtualenvs.create false

COPY ./pyproject.toml ./poetry.lock* ./
RUN poetry install
