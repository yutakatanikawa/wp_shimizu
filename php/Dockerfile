FROM wordpress:6.0.2-php8.0-fpm-alpine

RUN apk update \
    && apk add mysql-client \
    && rm -rf /var/cache/apk/*

COPY php.ini /usr/local/etc/php

# mailhog用の設定
RUN curl --location --output /usr/local/bin/mhsendmail https://github.com/mailhog/mhsendmail/releases/download/v0.2.0/mhsendmail_linux_amd64 \
    && chmod +x /usr/local/bin/mhsendmail

RUN echo 'sendmail_path="/usr/local/bin/mhsendmail --smtp-addr=mailhog:1025 --from=no-reply@docker.dev"' > /usr/local/etc/php/conf.d/mailhog.ini

WORKDIR /var/www/html
