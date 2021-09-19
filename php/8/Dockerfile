FROM php:8.0-fpm-buster

#更换源
RUN    sed -i "s/deb.debian.org/mirrors.aliyun.com/g" /etc/apt/sources.list 

#编译安装核心扩展 gd
RUN apt-get update &&\
    apt-get install -y     libfreetype6-dev libjpeg62-turbo-dev libpng-dev &&\
    docker-php-ext-configure gd --with-freetype --with-jpeg &&\
    docker-php-ext-install -j$(nproc) gd


RUN usermod -u 1000 www-data

RUN docker-php-ext-install mysqli pdo_mysql \
    && docker-php-ext-enable mysqli
    
#pecl 安装扩展 redis
RUN pecl install redis  &&  \
    docker-php-ext-enable redis && \


    pecl install swoole && \
    docker-php-ext-enable swoole && \

    docker-php-ext-install gd && \
    docker-php-ext-enable gd && \

    docker-php-ext-install opcache && \
    docker-php-ext-enable opcache && \

    pecl install mongodb && \
    docker-php-ext-enable mongodb


EXPOSE 9000


# 镜像信息
LABEL Author="kunl"
LABEL Version="2.0.0"
LABEL Description="PHP FPM 8 镜像. All extensions."


