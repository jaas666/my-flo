FROM python:3.12-slim-bookworm

ARG ESPHOME_VERSION=2026.9.1
ARG ESPTOOL_VERSION=5.3.1
ARG UID=1000
ARG GID=1000

RUN apt-get update \
    && apt-get install -y --no-install-recommends git curl ca-certificates build-essential \
    && rm -rf /var/lib/apt/lists/*

RUN groupadd --gid ${GID} dev \
    && useradd --uid ${UID} --gid ${GID} --create-home --shell /bin/bash dev

RUN pip install --no-cache-dir esphome==${ESPHOME_VERSION} esptool==${ESPTOOL_VERSION}

USER dev
RUN mkdir -p /home/dev/.cache/esphome
WORKDIR /workspace/esphome
