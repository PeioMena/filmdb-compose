FROM nginx:latest

RUN rm -rf /etc/nginx/user.conf.d/*
COPY conf.d/nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 8080

# FROM nginxproxy/nginx-proxy:0.9.1-alpine

# RUN rm -rf /etc/nginx/user.conf.d/*
# COPY conf.d/nginx.conf /etc/nginx/conf.d/default.conf