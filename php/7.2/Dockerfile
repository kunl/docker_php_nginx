# PHP 容器配置

# 从官方基础版本构建
FROM php:7.2-fpm
# 官方版本默认安装扩展:
# Core, ctype, curl
# date, dom
# fileinfo, filter, ftp
# hash
# iconv
# json
# libxml
# mbstring, mysqlnd
# openssl
# pcre, PDO, pdo_sqlite, Phar, posix
# readline, Reflection, session, SimpleXML, sodium, SPL, sqlite3, standard
# tokenizer
# xml, xmlreader, xmlwriter
# zlib

RUN usermod -u 1000 www-data

RUN docker-php-ext-install mysqli pdo_mysql \
    && docker-php-ext-enable mysqli
EXPOSE 9000


# 1.0.2 增加 bcmath, calendar, exif, gettext, sockets, dba,
# pcntl, shmop, sysvmsg, sysvsem, sysvshm 扩展
RUN docker-php-ext-install -j$(nproc) bcmath calendar exif gettext \
sockets dba pcntl shmop sysvmsg sysvsem sysvshm


# 1.0.22 redis 扩展
RUN pecl install redis && docker-php-ext-enable redis
RUN pecl install mongodb && docker-php-ext-enable mongodb

# 镜像信息
LABEL Author="kunl"
LABEL Version="1.0.0"
LABEL Description="PHP FPM 7.4 镜像. All extensions."
