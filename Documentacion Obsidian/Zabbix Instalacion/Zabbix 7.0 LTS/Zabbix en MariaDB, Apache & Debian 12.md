
---
# Documentación Oficial de Zabbix.

Documentación Debian/Ubuntu: [Documentacion Debian/Ubuntu](https://www.zabbix.com/documentation/current/es/manual/installation/upgrade/packages/debian_ubuntu)
Consigue Zabbix: [Documentacion para Obtener](https://www.zabbix.com/download?zabbix=7.0&os_distribution=debian&os_version=12&components=server_frontend_agent&db=pgsql&ws=apache)

---
# Información Adicional.

Dicha documentación se encuentra realizada con la versión de Zabbix 7.0 LTS, OS distribución debian 12.9.0-amd64, base de datos MariaDB (MySQL fue reemplazado) y servidor web apache.

---
# Preparar el Servidor.

---
## Paso 1: Iniciar sesión como `root`:

Como `sudo` no está instalado por defecto en algunas instalaciones mínimas de Debian, primero debes acceder como `root`:

```
su -
```

_Ingresa la contraseña de `root` cuando se te solicite._

Si no tienes la contraseña de `root`, puedes configurarla con `sudo passwd root` en sistemas donde `sudo` ya esté disponible.
## Paso 2: Actualizar el Servidor:

Ejecuta los siguientes comandos como `root`:

```
apt update && apt upgrade -y
```

_Esto actualiza la lista de paquetes e instala `sudo`._
## Paso 3: Instalar `sudo`:

```
apt install sudo -y
```
## Paso 4: Agregar tu usuario al grupo `sudo`:

Para que tu usuario pueda usar `sudo`, debes añadirlo al grupo `sudo`:

```
usermod -aG sudo tu_usuario
```

_Reemplaza `tu_usuario` con tu nombre de usuario real (ejemplo: `usermod -aG sudo admin`)._

**Verificación:**

```
groups tu_usuario
```

_Debe aparecer `sudo` en la lista de grupos._
## Paso 5: Cerrar Sesión y Reiniciar:

Para aplicar los cambios:

```
reboot
```

_O simplemente cierra y vuelve a abrir la terminal._
## Paso 6: Probar `sudo`:

Después de reiniciar, verifica que `sudo` funcione:

```
sudo whoami
```

_Si te pide tu contraseña y muestra `root`, ¡todo está correcto!_

---
# Instalación de Zabbix Server.

---
## Paso 7: Instalar repositorio de Zabbix:

```
wget https://repo.zabbix.com/zabbix/7.0/debian/pool/main/z/zabbix-release/zabbix-release_latest_7.0+debian12_all.deb
dpkg -i zabbix-release_latest_7.0+debian12_all.deb
apt update
```
## Paso 8: Install Zabbix server, frontend, agent:

```
apt install zabbix-server-mysql zabbix-frontend-php zabbix-apache-conf zabbix-sql-scripts zabbix-agent
```
## Paso 9: Instalar Base de Datos:

Para instalar MariaDB simplemente ejecuta:

```
sudo apt update
sudo apt install mariadb-server
```

Después de la instalación, puedes iniciar y habilitar el servicio:

```
sudo systemctl start mariadb
sudo systemctl enable mariadb
```

Y para asegurar la instalación y configurar seguridad inicial **OPCIONAL**:

```
sudo mysql_secure_installation
```
## Paso 10: Crear base de datos inicial

```
mysql -uroot -p
```

>password

```
create database zabbix character set utf8mb4 collate utf8mb4_bin;
```

La clave es de prueba, debes poner una real:

```
create user zabbix@localhost identified by 'password';
```

```
grant all privileges on zabbix.* to zabbix@localhost;
```

```
set global log_bin_trust_function_creators = 1;
```  

```
quit;
```
## Paso 11: En el host del servidor Zabbix, importe el esquema inicial y los datos. Se le pedirá que ingrese su contraseña recién creada:

```
zcat /usr/share/zabbix-sql-scripts/mysql/server.sql.gz | mysql --default-character-set=utf8mb4 -uzabbix -p zabbix
```
## Paso 12: Deshabilite la opción 'log_bin_trust_function_creators' después de importar el esquema de la base de datos:

```
mysql -uroot -p
```

> password

```
set global log_bin_trust_function_creators = 0;
```

```
quit;
```
## Paso 13: Configurar la base de datos para el servidor Zabbix:

Edita el archivo:  `/etc/zabbix/zabbix_server.conf`

```
nano /etc/zabbix/zabbix_server.conf
```

Busca `DBPassword=` y coloca la clave agregada a la base de datos:

> DBPassword=password
## Paso 14: Inicie los procesos del servidor y del agente de Zabbix:

Inicie los procesos del servidor y del agente Zabbix y haga que se inicien al iniciar el sistema.

```
systemctl restart zabbix-server zabbix-agent apache2
systemctl enable zabbix-server zabbix-agent apache2
```

**Otros Comandos que puedes emplear:**

Para iniciar el servidor de zabbix, luego de eso verifica el estatus del mismo:

```
systemctl start zabbix-server
```

Para verificar el estatus del servidor de zabbix:

```
systemctl status zabbix-server
```

Habilitar el agente de zaabbix:

```
systemctl enable zabbix-agent
```

Verificar el estatus del agent:

```
systemctl status zabbix-agent
```

Habilitar servidor:

```
systemctl enable zabbix-server
```

Reiniciar el Agente:

```
systemctl restart zabbix-agent.service
```

Reiniciar el zabbix server:

```
systemctl restart zabbix-server.service
```

Reiniciar el apache:

```
systemctl restart apache2.service
```
## Paso 15: Abrir la página web de la interfaz de usuario de Zabbix:

La URL predeterminada para la interfaz de usuario de Zabbix cuando se utiliza el servidor web Apache es http://host/zabbix

---
# Instalar Paquete de Idiomas.

Al aplicar el siguiente comando podrás buscar y seleccionar el paquete de idiomas que deseas:

```
sudo dpkg-reconfigure locales
```

Recomendación, busca: 

>`en_US.UTF-8 UTF-8`
>`es_ES.UTF-8 UTF-8`

Marca las opciones, acepta los cambios y reinicia los servicios y verifica en el servidor.
# Actualizar Versión de Zabbix

Primeramente debes descargar el repositorio de zabbix al que deseas actualizar, en este caso es el 7.2.

_Recomendación: Que sea un comando a la vez._

```
wget https://repo.zabbix.com/zabbix/7.2/release/debian/pool/main/z/zabbix-release/zabbix-release_latest_7.2+debian12_all.deb
```

```
dpkg -i zabbix-release_latest_7.2+debian12_all.deb
```

```
apt update && apt upgrade -y
```

Instala y actualiza el Zabbix Server, el FrontEnd, y el agent.

```
apt install --only-upgrade zabbix-server-mysql zabbix-frontend-php zabbix-apache-conf zabbix-sql-scripts zabbix-agent
```

Luego de aplicar la sintaxis previa, puede llegar a consultarte si quieres actualizar de igual forma los siguientes archivos:

> `/etc/zabbix/zabbix_server.conf`
> `/etc/zabbix/zabbix_agentd.conf`

Dile que no `n`, luego pantalla rosa con el "zabbix-server.service" dale "Ok"
# Actualizar Base de Datos

El motivo por el que falla es por un tema de versiones, por ende tendremos que actualizar la base de datos.
## Ingresa a MySQL

```
set global log_bin_trust_function_creators = 1;
```

Sal del MySQL.

```
quit;
```

Puedes visualizar la actualización usando:

```
tail -F /var/log/zabbix/zabbix_server.conf
```

Espera que se actualice solo y recarga la web, luego de eso ejecuta el siguiente comando.
## Nuevamente ingresa a MySQL.

Para restablecer la configuración establece:

```
set global log_bin_trust_function_creators = 0;
```

Sal del MySQL.

```
quit;
```

Ya estaría listo reinicia los servicios.

```
systemctl restart apache2.service
```

```
systemctl restart zabbix-server.service
```

```
systemctl restart zabbix-agent.service
```

Y por ultimo verifica el funcionamiento del servidor y la versión en uso.
# Instalar Certificado SSL para conexión por HTTPS.

Busca la ruta `/etc/apache2/listen.conf` y especifica el puerto por el cual trabajara.

>listen 80

En `ports.conf`establece el puerto:

> listen 80
> 

IfModule ssl_module
Listen 443

IfModule mod_gnutls.c
Listen 443

/etc/apache2/sites-available/default-ssl.conf

Buscar las siguientes lineas:
`# SSLCertificateFile /etc/ssl/certs/zabbix.crt'
`# SSLCertificateKeyFile /etc/ssl/private/zabbix.key`

Y quitar los '#' para descomentar.

Lo mismo con:

/etc/apache2/sites-available/enable-ssl.conf

`# SSLCertificateFile /etc/ssl/certs/zabbix.crt`
`# SSLCertificateKeyFile /etc/ssl/private/zabbix.key`