
---
# Documentación Oficial de Zabbix.

Documentación Debian/Ubuntu: [Documentacion Debian/Ubuntu](https://www.zabbix.com/documentation/current/es/manual/installation/upgrade/packages/debian_ubuntu)
Consigue Zabbix: [Documentacion para Obtener](https://www.zabbix.com/download?zabbix=7.0&os_distribution=debian&os_version=12&components=server_frontend_agent&db=pgsql&ws=apache)

---
# Información Adicional.

Dicha documentación se encuentra realizada con la versión de Zabbix 7.0 LTS, OS distribución Ubuntu 24.04.1, base de datos MySQL y servidor web apache.

---
# Preparar el Servidor.

---
## Paso 1: Cambiar a `sudo`:

En el CLI, luego de `user@machine:~$ ` coloca la siguiente comando:

```
sudo -i
```

Al darle "Enter" te pedirá la clave del usuario "sudo" (Si es que tiene clave) `[sudo] password for user:` ingresa la misma y dale "Enter", luego de estarás en como sudo y lo comprobaras de la siguiente manera:
```
root@machine:
```

_Nota: Con este comando se puede ingresar como sudo `sudo -s`._
## Paso 2: Actualizar el Servidor.

Utiliza el siguiente comando para actualizar el servidor, paquetes, dependencias, entre otros:

```
apt update && apt upgrade -y
```

---
# Instalación de Zabbix Server.

---
## Paso 3: Instale el repositorio de Zabbix:

 ```
wget https://repo.zabbix.com/zabbix/7.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest+ubuntu24.04_all.deb
dpkg -i zabbix-release_latest+ubuntu24.04_all.deb
apt update
```
## Paso 4: Instala Zabbix Server, el FrontEnd, y el agent:

```
apt install zabbix-server-mysql zabbix-frontend-php zabbix-apache-conf zabbix-sql-scripts zabbix-agent
```
## Paso 5: Instalar Base de Datos:

Instala mysql server:

```
apt install mysql-server
```
## Paso 6: Crea la Base de Datos

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
## Paso 7: En el host del servidor Zabbix, importe el esquema inicial y los datos. Se le pedirá que ingrese su contraseña recién creada:

```
zcat /usr/share/zabbix-sql-scripts/mysql/server.sql.gz | mysql --default-character-set=utf8mb4 -uzabbix -p zabbix
```
## Paso 8: Deshabilite la opción 'log_bin_trust_function_creators' después de importar el esquema de la base de datos:

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
## Paso 9: Configure la base de datos para el servidor Zabbix:

Edita el siguiente archivo `/etc/zabbix/zabbix_server.conf`, utiliza el editor nano:

```
nano /etc/zabbix/zabbix_server.conf
```

Busca `DBPassword=` y coloca la clave agregada a la base de datos:

> DBPassword=password
## Paso 10: Inicie los procesos del servidor y del agente de Zabbix:

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
## Paso 11: Abrir la página web de la interfaz de usuario de Zabbix:

La URL predeterminada para la interfaz de usuario de Zabbix cuando se utiliza el servidor web Apache es http://host/zabbix
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