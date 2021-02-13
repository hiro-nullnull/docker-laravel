# Composerコマンドのインストール
# Laravelで必要なPHP拡張機能のインストール（bcmath, pdo_mysqlが不足してるから追加インストール）

# docker hub の公式イメージをベースイメージとする
FROM php:7.4-fpm-buster
# SHELLをbashに指定 オプションについてはこちら : https://matsuand.github.io/docs.docker.jp.onthefly/engine/reference/builder/#shell
SHELL ["/bin/bash", "-oeux", "pipefail", "-c"]

# コンテナ内のサーバー環境変数
ENV COMPOSER_ALLOW_SUPERUSER=1 \
  COMPOSER_HOME=/composer

# composer をコピーする？
COPY --from=composer:1.10 /usr/bin/composer /usr/bin/composer

# Debian系のパッケージ管理なのでapt-getで必要なものをインストール
RUN apt-get update && \
  apt-get -y install git unzip libzip-dev libicu-dev libonig-dev && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/* && \
  docker-php-ext-install intl pdo_mysql zip bcmath

COPY ./php.ini /usr/local/etc/php/php.ini

WORKDIR /work
