# docker-laravel
dockerでLaravel環境を構築してみる

## git clone後
アクセス : 127.0.0.1:10080

>ビルドしてコンテナを起動

docker-compose up -d --build

>起動したアプリケーションコンテナにログインし必要なパッケージをインストール

docker-compose exec app bash

composer install


>.env ファイルがなくて怒られるのでコピーして作成

cp backend/.env.example backend/.env

>APP_KEYがなくて怒られるので作成(コンテナ内で実行)

docker-compose exec app bash

php artisan key:generate
