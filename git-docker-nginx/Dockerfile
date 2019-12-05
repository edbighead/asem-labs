FROM nginx:1.17.6

WORKDIR /home/user

RUN apt-get update && apt-get install -y \
    vim git\
    && rm -rf /var/lib/apt/lists/* \
    && rm -rf /etc/nginx/conf.d

COPY conf.d /etc/nginx/conf.d

EXPOSE 80

STOPSIGNAL SIGTERM

CMD ["nginx", "-g", "daemon off;"]