FROM webdevops/php-nginx-dev:8.2-alpine

ARG LOCAL_UID
ARG LOCAL_GID

WORKDIR /var/www/localhost
COPY . .

# Uncomment these commented lines if your local UID isn't 1000:
#RUN addgroup -g ${LOCAL_GID} myusergroup && \
#    adduser -u ${LOCAL_UID} -G myusergroup -D myuser

RUN chown -R ${LOCAL_UID}:${LOCAL_GID} .