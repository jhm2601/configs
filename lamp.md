# Configurar lamp en wsl

Sudo apt-get update

# configurar apache2

Sudo apt-get install apache2

# configuracion de mysql

Ir a https://www.mysql.com/downloads/
Buscar MySQL Community (GPL) Downloads »
Luego seleccionar la opción MySQL APT Repository

Decargar el .deb de mysql en la versión que se vaya a utilizar
Copiar el archivo el ir la la carpeta a la izquierda de Linux
Ir a Ubuntu/home/username/
Pegar dentro de esa dirección
Hacer ls en la terminal para verificar que se pego
Hacer sudo dkpg -i nombre_del_archivo_mysql
En configuration mysql-apt-config dar al boton de OK
sudo apt-get update
sudo apt-get install mysql-server

aqui paso intermedio configurar root password de mysql


# este comando es opcional (tambien tiene que ver con mysql)
sudo mysql_secure_installation

VALIDATE PASSWORD COMPONENT can be used to test passwords and improve security. It checks thefu strength of passsoerd….
Would you like to setup VALIDATE PASSWORD component?

Presionar “y”

Pide otro password

Tambien y y y

# instalar php y otras dependencias
sudo apt install php php-cgi php-mysqli php-pear php-mbstring libapache2-mod-php php-common php-phpseclib php-mysql -y

# instalar repositorio principal de php
sudo add-apt-repository ppa:ondrej/php

# revisar instalaciones relacionadas con php instaladas en el sistema linux
sudo dpkg --get-selections | grep php


# es posible instalar varias versiones
sudo apt install php8.0
sudo apt install php7.4


# Dar permisos para copier y pegar en la carpeta www
Dell es mi usuario de Ubuntu
Sudo chown -R dell /var/www

