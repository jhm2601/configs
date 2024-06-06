## configurar el archivo del hosts 

Ir a sudo nano /etc/hosts
agregar dentro la configuracion de la web
127.0.0.1   dev.webs.com
crtl + X y guardar

## configurar el archivo de available site

ir a cd /etc/apache2/sites-available/
vamos a crear un archivo que se llame como pusimos en el host con la terminacion de config
Ejemplo
sudo touch dev.webs.com.conf
accedemos a modificarlo

sudo nano dev.webs.com.conf

agregar esto de abajo

<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName dev.fischer.com
    DocumentRoot /var/www/html/fischer/public

    <Directory /var/www/html/fischer/public>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

guardar el archivo.

Luego corremos esto para que apache renocozca esta config
sudo a2ensite dev.fischer.com

al final reinicioar el servidor.
