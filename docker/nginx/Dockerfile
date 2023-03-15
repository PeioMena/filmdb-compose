FROM nginx:1.23.3-alpine-slim

RUN rm -rf /etc/nginx/user.conf.d/*
COPY conf.d/nginx.conf /etc/nginx/conf.d/nginx.conf