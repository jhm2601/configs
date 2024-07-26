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

` <VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName example.local
    DocumentRoot /var/www/html/example/public

    <Directory /var/www/html/example/public>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost> `

guardar el archivo.

Luego corremos esto para que apache renocozca esta config
sudo a2ensite example.config

`sudo /etc/init.d/apache2 reload`

al final reinicioar el servidor.

### modificar archivo host

`sudo nano /etc/hosts`
dentro agregar 127.0.0.1 example.local

[Descargar host file editor](https://hostsfileeditor.com/)

abrir el programa y configurar alli los host como en el archivo de host
127.0.0.1     example.local
::1           example.local

En la raiz del usuario de windows C:\Users\juanh hay que crear un archivo .wslconfig

Dentro del archivo hay que colocal el seguiente contenido

`[wsl2]

memory=4GB      # Limits VM memory in WSL 2 up to 4GB
processors=4    # Makes the WSL 2 VM use two virtual processors
localhostForwarding=true`
