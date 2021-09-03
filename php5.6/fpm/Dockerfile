FROM alpine:latest
RUN apk add nginx && rm -rf /var/cache/apk/*
COPY conf/default.conf /etc/nginx/sites-available/default.conf
CMD ["nginx", "-g", "daemon off;"]
