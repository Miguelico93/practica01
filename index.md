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

'sudo systemctl restart apache2.service'

Paso 4: Instale PHP Y Módulos Relacionados
Ejecute los comandos a continuación para instalar PHP y los módulos PHP relacionados.

'sudo apt-get install php php-cgi libapache2-mod-php php-common php-pear php-mbstring'

Paso 5: Configurar Apache2 Para Usar PHP
Después de instalar PHP y otros scripts relacionados, ejecute los siguientes comandos para permitir que Apache2 use PHP.

'sudo a2enconf php7.2-cgi'

Recargar apache2

'sudo systemctl reload apache2.service'

Paso 6: Instalar PhpMyAdmin
Ahora que Apache2 y PHP están instalados, el último paso es instalar phpMyAdmin y configurar. Para hacer eso, ejecute los siguientes comandos

'sudo apt-get install phpmyadmin php-gettext'

Cuando se le solicite que elija el servidor web, seleccione apache2 y continúe.
Cuando se le solicite nuevamente, permitir que debconfig-common instale una base de datos y configure seleccionar No.
Después de la instalación, ejecute los comandos a continuación para iniciar sesión en el servidor de la base de datos para habilitar el inicio de sesión raíz de phpMyAdmin.
Ahora, abra su navegador web e inicie sesión en el nombre de host o la dirección IP del servidor seguido de phpmyadmin

## Instalación de composer.

Instalando compositor
Para instalar Composer en su sistema Ubuntu, siga estos pasos:

Antes de descargar e instalar Composer, primero actualice el índice de paquetes e instale los requisitos necesarios:

'sudo apt update'
'sudo apt install wget php-cli php-zip unzip'

Ahora que tenemos instalado php cli en nuestra máquina, podemos descargar el instalador del compositor con:

'php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"'

El comando anterior descargará el composer-setup.phparchivo en el directorio de trabajo actual.

A continuación, debemos verificar la integridad de los datos del script comparando el SHA-384hash del script con el último hash del instalador que se encuentra en la página de Firmas / claves públicas del editor .

Usaremos el siguiente comando wget para descargar la firma esperada del último instalador de Composer desde la página de Github del Compositor y almacenarla en una variable llamada HASH:

'HASH="$(wget -q -O - https://composer.github.io/installer.sig)"'

Ahora ejecute el siguiente comando para verificar que el script de instalación no esté dañado:

'php -r "if (hash_file('SHA384', 'composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"'

Si los hashes coinciden, verá la siguiente salida:

'Installer verified'

Si los hashes no coinciden verás Installer corrupt. En este caso, deberá volver a descargar el script de instalación de Composer y volver a verificar el valor de la $HASHvariable con echo $HASH. Una vez que se verifique el instalador, puede continuar con el siguiente paso.

El siguiente comando instalará Composer en el /usr/local/bindirectorio:

'sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer'

All settings correct for using Composer
'Downloading...'

Composer (version 1.7.2) successfully installed to: /usr/local/bin/composer
'Use it: php /usr/local/bin/composer'

Se composerinstala como un comando de todo el sistema y estará disponible para todos los usuarios.

El último paso es verificar la instalación:

'composer'

El comando anterior imprimirá la versión, los comandos y los argumentos del compositor.

## Como Instalar Adminer


### Paso 1
Necesitamos instalar apache2 y mysql-server a menos que lo esté instalando en un servidor web existente.

Actualizar y actualizar el servidor

'sudo apt update && sudo apt upgrade -y'

Instale el servidor Apache, PHP y MYSQL y algunas extensiones de PHP

sudo apt install apache2 php php-curl php-cli php-mysql php-gd mysql-client mysql-server -y
Asegure su instalación de MySQL y establezca la contraseña de root

'sudo mysql_secure_installation'

Desde aquí, solo puede presionar Y y luego ENTER para aceptar los valores predeterminados para todas las preguntas subsiguientes.

Puede configurar el usuario root para que use la contraseña mysql_native_password en su lugar para solucionar este problema, y tendremos que configurar la contraseña de root nuevamente para corregirlo.

Inicie sesión como sudo en mysql utilizando el nombre de usuario y la contraseña establecidos anteriormente.

'sudo mysql -u root'

en MySQL ingrese lo siguiente

'USE mysql;
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';

Por seguridad, haga que esta contraseña sea diferente a la contraseña de su servidor y no use al usuario root en ninguna aplicación que requiera una base de datos para almacenar y extraer datos.

FLUSH PRIVILEGES;
exit;'
### Paso 2
Descargamos el Adminer más reciente en nuestra carpeta raíz de servidores web Apache

'sudo mkdir /usr/share/adminer'.
'sudo wget "http://www.adminer.org/latest.php" -O /usr/share/adminer/latest.php'.
'sudo ln -s /usr/share/adminer/latest.php /usr/share/adminer/adminer.php'.
'echo "Alias /adminer.php /usr/share/adminer/adminer.php" | sudo tee /etc/apache2/conf-available/adminer.conf'.
'sudo a2enconf adminer.conf'.

Recarga la configuracion de apache

'sudo systemctl reload apache2'
Eso es acceder a la interfaz de administrador en
'http://<Server_IP_or_Domain>/adminer.php'


## Instalar GoAccess

### Paso 1

La primera alternativa, la cual usaremos en este tutorial, es a través del recurso oficial de GoAccess, para ello, descargaremos la última versión de GoAccess usando el comando wget de la siguiente forma:
'wget http://tar.goaccess.io/goaccess-1.2.tar.gz'

### Paso 2

Procedemos a extraer el archivo descargado ejecutando:
'sudo tar -xzvf goaccess-1.2.tar.gz'

### Paso 3

Ahora, cambiaremos el directorio a goaccess-1.2 y compilaremos GoAccess ejecutando el siguiente comando:
'cd goaccess-1.2'
'sudo ./configure --enable-utf8 --enable-geoip=legacy'
 
### Paso 4

Ahora ejecutamos:
sudo make

### Paso 5

Finalmente instalamos GoAccess ejecutando:
sudo make install

### Paso 6

La segunda alternativa para instalar GoAccess es a través de un repositorio, para ello será necesario descargar el repositorio de GoAccess usando apt con el siguiente comando:
echo "deb http://deb.goaccess.io/ $(lsb_release -cs) main" | sudo tee -a /etc/apt/sources.list.d/goaccess.list
wget -O - https://deb.goaccess.io/gnugpg.key | sudo apt-key add –

### Paso 7

Luego, actualizaremos el repositorio usando el siguiente comando:
sudo apt-get update -y
### Paso 8

Finalmente, instalamos GoAccess ejecutando:
'sudo apt-get install goaccess -y' 


## Control de acceso a un directorio con .htaccess

Creamos un directorio llamado stats dentro del directorio /var/www/html. El acceso a este directorio deberá estar controlado y solo se podrá acceder mediante un usuario y una contraseña.

### Paso 1

Creamos el directorio stats

```
mkdir /var/www/html/stats
```

### Paso 2

Lanzamos el proceso de goaccess en background para generar los informes en segundo plano

```
goaccess /var/log/apache2/access.log -o /var/www/html/stats/index.html --log-format=COMBINED --real-time-html &
```

### Paso 3

Creamos el archivo de contraseñas para el usuario que accederá al directorio stats. El archivo de contraseñas lo guardamos en un directorio seguro. En nuestro caso lo podemos guardar en /home/usuario

```
htpasswd -c /var/www/htpasswd/hostname inda
```

### Paso 4

Creamos el archivo .htaccess en el directorio que queremos proteger con usuario y contraseña. En nuestro caso lo vamos a crear en el directorio /var/www/html/stats/.htaccess

```
/var/www/html/stats/.htaccess
```

El contenido del archivo .htaccess será el siguiente:

```
<Directory /var/www/htpasswd/logs>
AuthType Basic
AuthName "Acceso Restringido"
AuthUserFile /var/www/htpasswd/hostname
Require user inda
</Directory>
```

### Paso 5

Editamos el archivo configuración de Apache

```
nano /etc/apache2/sites-enabled/000-default.conf
```

Añadimos la siguiente sección dentro de las etiquetas de <VirtualHost *:80> y </VirtualHost>


```
<Directory "/var/www/html/stats">
  Options Indexes FollowSymLinks
  AllowOverride All
  Require all granted
</Directory>
```

### Paso 6

Reiniciamos el servicio de Apache

```
`systemctl restart apache2
```





