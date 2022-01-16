# Copyright (C) 2019 Sebastian Pipping <sebastian@pipping.org>
# Licensed under the BSD License (3 clause, also known as the new BSD license)

FROM python:3.8-slim

ENV PATH=${PATH}:/root/.local/bin

RUN apt-get update && apt-get install --yes --no-install-recommends \
        wait-for-it

RUN pip3 install django django_celery_beat django_enum_choices

WORKDIR /

RUN django-admin startproject setups_project

WORKDIR /setups_project/

RUN python3 manage.py startapp setups

COPY setups setups
COPY settings.py setups_project/settings.py
COPY docker/entrypoint.sh  /
