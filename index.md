# practica01
## Instalacion de pila LAMP 
### Instalación de Ubuntu Server
Lo primero que haremos sera instalar una maquina de ubuntu server y cuando la tengamos actualizaremos el sistema con el comando:

'apt update' para descargar las actualizaciones y despues 'apt upgrade' para hacer la instalacion de la actualizació.

### Instalación de Apache
Para instalarlo utilizaremos el comando de instalacion de ubuntu 'apt install apache2' como administrador o en caso que no lo seamos pondremos delante 'sudo ...'.

Para iniciar el servidio tenemos el comando: 'systemctl start apache2'.
Para parar el servicion emplearemos: 'systemctl stop apache2'.
Para ver el estado del servicio: 'systemctl status apache2'.
Y para reiniciarlo emplearemos: 'systemctl restart apache2'.

### Instalación de MySQL Server

Para instalarlo emplearemos el comand: 'apt install mysql-server'

#### Archivos de configuración de MySQL Server
'/etc/mysql/mysql.cnf'

También podemos encontrar archivos de configuración en los directorios:

'/etc/mysql/conf.d/'
'/etc/mysql/mysql.conf.d/'

#### Como acceder a mysql sever como root

Nos metemos como root con el comando'sudo su'.

Una vez iniciada la sesion como root iniciamos la consola de mysql
