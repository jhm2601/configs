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

## otras instalaciones de php
sudo apt install php8.2-common php8.2-mysql php8.2-xml php8.2-xmlrpc php8.2-curl php8.2-gd php8.2-imagick php8.2-cli php8.2-dev php8.2-imap php8.2-mbstring php8.2-opcache php8.2-soap php8.2-zip php8.2-redis php8.2-intl

### instalar mysql

```
sudo apt-get install -y mysql-server php-mysql
sudo service mysql restart
sudo mysql_secure_installation
    #> Validate password component: N
    #> New password: MyPassword
    #> Remove anonymous users: Y
    #> Disallow root login remotely: Y
    #> Reload privilege tables now: Y
sudo service mysql stop
sudo usermod -d /var/lib/mysql mysql
sudo service mysql start ```

# revisar instalaciones relacionadas con php instaladas en el sistema linux
sudo dpkg --get-selections | grep php


# es posible instalar varias versiones
sudo apt install php8.0
sudo apt install php7.4


# Dar permisos para copier y pegar en la carpeta www
Dell es mi usuario de Ubuntu
Sudo chown -R dell /var/www

