FROM php:7.4-cli-alpine

COPY --from=composer:2 /usr/bin/composer /usr/local/bin/composer

ENV COMPOSER_ALLOW_SUPERUSER=1
RUN /usr/local/bin/composer global config allow-plugins.dealerdirect/phpcodesniffer-composer-installer true
RUN /usr/local/bin/composer global require dealerdirect/phpcodesniffer-composer-installer:*

RUN /usr/local/bin/composer global require magento/magento-coding-standard:*

RUN echo memory_limit = -1 >> /usr/local/etc/php/conf.d/custom-memory.ini

ADD problem-matcher.json /problem-matcher.json
ADD entrypoint.sh /entrypoint.sh
RUN ["chmod", "+x", "/entrypoint.sh"]
ENTRYPOINT ["/entrypoint.sh"]
