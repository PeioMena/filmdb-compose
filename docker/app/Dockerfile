FROM python:3.10.4-alpine 

# This prevents Python from writing out pyc files
ENV PYTHONDONTWRITEBYTECODE=1
# This keeps Python from buffering stdin/stdout
ENV PYTHONUNBUFFERED=1
ENV APP_HOME=/app

WORKDIR $APP_HOME
RUN mkdir src run
COPY requirements.txt $APP_HOME
COPY ../../run $APP_HOME/run/

RUN apk add libc-dev mariadb-dev mariadb-connector-c-dev gcc python3-dev git
RUN python -m pip install --upgrade pip 
RUN pip install -r requirements.txt

# EXPOSE 8080
# EXPOSE 8090
ENTRYPOINT [ "./run/entrypoint.sh" ]