# sandbox的に使うので軽量イメージを使う
FROM python:3.11.8-bullseye

ENV TZ=Asia/Tokyo
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

ENV PYTHONPATH "${PYTHONPATH}:/workspace"
WORKDIR /workspace

RUN pip install poetry \
    && poetry config virtualenvs.create false

# ENV POETRY_HOME=/opt/poetry
# RUN curl -sSL https://install.python-poetry.org/ | python - --version 1.7.1 && \
#     cd /usr/bin && \
#     ln -s /opt/poetry/bin/poetry && \
#     poetry config virtualenvs.create false

COPY ./test/pyproject.toml ./test/poetry.lock* ./
RUN poetry install
