FROM python:3.10.10-alpine 

# remove this when uwsgi is required 
# # This prevents Python from writing out pyc files
ENV PYTHONDONTWRITEBYTECODE=1
# # This keeps Python from buffering stdin/stdout
ENV PYTHONUNBUFFERED=1

ENV APP_HOME=/app

WORKDIR $APP_HOME
RUN mkdir src bin
COPY ./docker/app/production/prod_requirements.txt $APP_HOME
COPY ./docker/app/bin $APP_HOME/bin

WORKDIR $APP_HOME/src

RUN apk update 
# mysqlclient instalazioan errorea kentzeko (alpine irudia bada)
RUN apk add --virtual build-deps gcc python3-dev musl-dev 
RUN apk add --no-cache mariadb-dev
# git instalatu (alpine irudia bada)
RUN apk add git
RUN git clone https://oauth2:glpat-zDqyQZRrfbmQkqk-RCWo@gitlab.com/codesyntax/filmdb 

WORKDIR $APP_HOME
# not necessary with python:latest image
# RUN apk add libc-dev mariadb-dev mariadb-connector-c-dev gcc python3-dev git 
RUN python -m pip install --upgrade pip 
RUN pip install -r prod_requirements.txt


ENTRYPOINT [ "./bin/entrypoint.sh" ]