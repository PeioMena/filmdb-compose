FROM python:3.10.10-alpine 

# # This prevents Python from writing out pyc files
ENV PYTHONDONTWRITEBYTECODE=1
# # This keeps Python from buffering stdin/stdout
ENV PYTHONUNBUFFERED=1

ENV APP_HOME=/app

WORKDIR $APP_HOME
RUN mkdir src bin
COPY ./docker/app/requirements.txt $APP_HOME
COPY ./docker/app/bin $APP_HOME/bin
COPY ./src $APP_HOME/src

RUN apk update 
# mysqlclient instalazioan errorea kentzeko (alpine irudia bada)
RUN apk add --virtual build-deps gcc python3-dev musl-dev 
RUN apk add --no-cache mariadb-dev
RUN python -m pip install --upgrade pip 
RUN pip install -r requirements.txt


ENTRYPOINT [ "./bin/entrypoint.sh" ]