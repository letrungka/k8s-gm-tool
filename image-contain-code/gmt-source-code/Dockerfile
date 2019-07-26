FROM composer:1.7.3 as build
WORKDIR /app
COPY ./group-management-tool/. /app
RUN apk add gmp-dev \
&& apk add yarn \
&& docker-php-ext-configure gmp \
&& docker-php-ext-install gmp \
&& composer install \
&& yarn install \
&& yarn run prod 
FROM letrungka/php-webserver:1.2
COPY --from=build /app /app