# mcr
parser .xlsx, creator .xml feed


х. Переименовать/скопировать файл .env.example -> .env и установить в нем необходимые значения переменных окружения


x+1. Разворачивание структуры БД
```
docker ps -a;
# example result:
# CONTAINER ID   IMAGE        COMMAND                  CREATED             STATUS             PORTS                                                                            NAMES
# 19cd970f4951   mcr-nginx    "/docker-entrypoint.…"   About an hour ago   Up About an hour   0.0.0.0:8888->80/tcp, :::8888->80/tcp, 0.0.0.0:8443->443/tcp, :::8443->443/tcp   mcr-nginx
# 611fc6d6d06d   mcr-phpfpm   "docker-php-entrypoi…"   About an hour ago   Up About an hour   9000/tcp                                                                         mcr-phpfpm
# c6f72a16409e   mcr-mysql    "docker-entrypoint.s…"   About an hour ago   Up About an hour   33060/tcp, 0.0.0.0:33306->3306/tcp, :::33306->3306/tcp                           mcr_mysql
# copy value from column 'CONTAINER_ID' from row where column 'NAMES' has value 'mcr_mysql'
# in this example - CONTAINER_ID = c6f72a16409e

cat dump.sql | docker exec -i {CONTAINER_ID} /usr/bin/mysql -u root --password=MYSQL_ROOT_PASSWORD MYSQL_DATABASE
# MYSQL_ROOT_PASSWORD, MYSQL_DATABASE - заменить на значения из файла .env
```