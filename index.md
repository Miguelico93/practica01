# practica01
## Instalacion de pila LAMP 
### Instalación de Ubuntu Server
Lo primero que haremos sera instalar una maquina de ubuntu server y cuando la tengamos actualizaremos el sistema con el comando: `apt update` para descargar las actualizaciones y despues `apt upgrade` para hacer la instalacion de la actualización.

### Instalación de Apache
Para instalarlo utilizaremos el comando de instalacion de ubuntu `apt install apache2` como administrador o en caso que no lo seamos pondremos delante `sudo ...`.

* Para iniciar el servicio tenemos el comando: `systemctl start apache2`.
* Para parar el servicio emplearemos: `systemctl stop apache2`.
* Para ver el estado del servicio: `systemctl status apache2`.
* Y para reiniciarlo emplearemos: `systemctl restart apache2`.

### Instalación de MySQL Server

Para instalarlo emplearemos el comando: `apt install mysql-server`

#### Archivos de configuración de MySQL Server
`/etc/mysql/mysql.cnf`

También podemos encontrar archivos de configuración en los directorios:

```
/etc/mysql/conf.d/
/etc/mysql/mysql.conf.d/
```

#### Como acceder a mysql sever como root

Nos metemos como root con el comando `sudo su`.

Una vez iniciada la sesion como root iniciamos la consola de mysql

### Instalación de módulos PHP

'sudo apt install php libapache2-mod-php php-mysql'

Para averiguar lo que hace el módulo libapache2-mod-php, podríamos escribir esto:

'sudo apt show libapache2-mod-php'

Comprobar que la instalación se ha realizado correctamente
Crea un archivo llamado 'info.php' en el directorio '/var/www/html'.

'sudo nano /var/www/html/info.php'

Añade el siguiente contenido:

 <? php

phpinfo ();

?>

Ahora accede desde un navegador a la URL: http://localhost/info.php

## Instalar PhpMyAdmin

Paso 1: Instalar El Servidor De Base De Datos MySQL
Ejecute los comandos a continuación para instalar el servidor de base de datos MySQL

actualización de sudo apt
sudo apt instalar mysql-server mysql-client
Durante la instalación, se le pedirá que cree y confirme la contraseña de root de MySQL.

Paso 2: Instalar El Servidor HTTP Apache2
A continuación, ejecute los comandos para instalar el servidor web HTTP Apache2.

'sudo apt install apache2'

Paso 3: Configurar Apache2
Ahora ejecute los siguientes comandos para configurar los ajustes básicos de Apache2.

Primero, confirme que la configuración de su servidor Ubuntu tenga definidas las directivas Apache2  DirectoryIndex para php . Para ejecutar aplicaciones basadas en PHP, Apache2 debe tener index.php como un índice de directorio en su archivo dir.conf.

'sudo nano /etc/apache2/mods-enabled/dir.conf'

Asegúrese de que index.php esté definido como un IndexIndex en el archivo dir.conf ...

'<IfModule mod_dir.c>
DirectoryIndex index.html index.php index.xhtml index.htm
</IfModule>'
A continuación, configure su dominio o nombre de servidor para su sitio ... Abra el archivo de configuración del sitio predeterminado de Apache2 ejecutando los siguientes comandos.

'sudo nano /etc/apache2/sites-enabled/000-default.conf'

Luego agregue ServerName y ServerAlias para que coincidan con su nombre de dominio ... y guarde el archivo.

'<VirtualHost *: 80>
     ServerAdmin admin@mylab.com
     DocumentRoot / var / www / html /
     ServerName example.com 
     ServerAlias example.com

     ErrorLog $ {APACHE_LOG_DIR} /error.log
     CustomLog $ {APACHE_LOG_DIR} /access.log combinado
</VirtualHost>'
Después de que reinicie Apache2.

sudo systemctl restart apache2.service

Paso 4: Instale PHP Y Módulos Relacionados
Ejecute los comandos a continuación para instalar PHP y los módulos PHP relacionados.

sudo apt-get install php php-cgi libapache2-mod-php php-common php-pear php-mbstring

Paso 5: Configurar Apache2 Para Usar PHP
Después de instalar PHP y otros scripts relacionados, ejecute los siguientes comandos para permitir que Apache2 use PHP.

sudo a2enconf php7.2-cgi

Recargar apache2

sudo systemctl reload apache2.service

Paso 6: Instalar PhpMyAdmin
Ahora que Apache2 y PHP están instalados, el último paso es instalar phpMyAdmin y configurar. Para hacer eso, ejecute los siguientes comandos

sudo apt-get install phpmyadmin php-gettext

Cuando se le solicite que elija el servidor web, seleccione apache2 y continúe.

Cuando se le solicite nuevamente, permitir que debconfig-common instale una base de datos y configure seleccionar No.

Después de la instalación, ejecute los comandos a continuación para iniciar sesión en el servidor de la base de datos para habilitar el inicio de sesión raíz de phpMyAdmin.

Ahora, abra su navegador web e inicie sesión en el nombre de host o la dirección IP del servidor seguido de phpmyadmin




