
# Установка

### Запуск и сборка окружения
    docker-compose up --build

### Структура приложения
    |-mysql
        |-config
            |-my.cnf
        |-data
        |-dump
    |-php
        |-apache
            |-certs
            |-logs
            |-sites
        |-Dockerfile
        |-php.ini
    |-phpmyadmin
    |-src
    |-docker-compose.yml
    |-README.md

### Создание SSL Сертификата

#### Генерируем ключ безопасности
    openssl genrsa -out server.key 2048
#### Генерируем файл на запрос сертификата
    openssl req -new -key server.key -out %имя_вашего_сайта%.csr
#### Создаем самоподписанный сертификат
    openssl x509 -req -extensions v3_req -days 365 -in %your_website%.csr -signkey server.key -out %your_website%.crt
***
#### Нюансы
1. Сертификаты SSL кладем в папку `php/apache/certs` именя сертификатов идентичны (`server.key, server.crt`).
2. Настройка для хоста в папке `php/apche/sites`
3. Что бы сразу поднять все базы в mysql кидаем sql файлы в `mysql/dump`. Доступ к базе: `root` : `123456`
