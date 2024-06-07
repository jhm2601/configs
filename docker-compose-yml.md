# ./docker-compose.yml
services:
    fischer_db:
        container_name: fischer_db
        image: mariadb:10.5.8
        volumes:
            - fischer_db_mysql:/var/lib/mysql
        command: mysqld --sql_mode=""
        environment:
            MYSQL_ROOT_PASSWORD: root
            MYSQL_DATABASE: fischer
            MYSQL_USER: fischer
            MYSQL_PASSWORD: fischer
        ports:
            - "9906:3306"
    fischer_nginx_php:
        build:
            context: ./.docker-php
        #image: php:7.4-apache
        container_name: fischer_nginx_php
        depends_on:
            - fischer_db
        volumes:
            - .:/var/www/html/
        ports:
            - "80:80"
        stdin_open: true
        tty: true
    phpmyadmin:
        image: phpmyadmin/phpmyadmin
        user: $UID:$GID
        sysctls:
            - net.ipv4.ip_unprivileged_port_start=0
        environment:
            - MYSQL_ROOT_PASSWORD=root
            - PMA_HOST=fischer_db
            - APACHE_RUN_USER=#$UID
            - APACHE_RUN_GROUP=#$GID
            - PMA_ARBITRARY=1
        depends_on:
            - fischer_db
        ports:
            - 8080:80
volumes:
    fischer_db_mysql:
