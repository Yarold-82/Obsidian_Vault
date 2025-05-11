[Documentacion Debian/Ubuntu](https://www.zabbix.com/documentation/current/es/manual/installation/upgrade/packages/debian_ubuntu)
## Paso 1: Cambiar a sudo.

En el CLI, luego de `user@machine:~$ ` coloca la siguiente comando:
```
sudo -i
```

Al darle "Enter" te pedirá la clave del usuario "sudo" (Si es que tiene clave) `[sudo] password for user:` ingresa la misma y dale "Enter", luego de estarás en como sudo y lo comprobaras de la siguiente manera:
```
root@machine:
```

Nota: Con este comando se puede ingresar como sudo `sudo -s`.
## PASO 2: Actualizar el Servidor.

Utiliza el siguiente comando para actualizar el servidor, paquetes, dependencias, entre otros:
```
apt update && apt upgrade -y
```
## Paso 3: Instale el repositorio de Zabbix.

 ```
wget https://repo.zabbix.com/zabbix/7.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest+ubuntu24.04_all.deb
dpkg -i zabbix-release_latest+ubuntu24.04_all.deb
apt update
```
## Paso 4: Instala Zabbix Server, el FrontEnd, y el agent.

```
apt install zabbix-server-mysql zabbix-frontend-php zabbix-apache-conf zabbix-sql-scripts zabbix-agent
```
## Paso 5: Verificar los Servicios del Zabbix y Activar los Correspondientes.

Para verificar el estatus del Zabbix:
```
systemctl status zabbix-server
```

Para iniciar el servidor, luego de eso verifica el estatus del mismo:
```
systemctl start zabbix-server
```

Verificar el estatus del agent:
```
systemctl status zabbix-agent
```

Habilitar el agente:
```
systemctl enable zabbix-agent
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
## Paso 6: Crea la Base de Datos

Instala mysql server:
```
apt install mysql-server
```

Luego de eso debes ingresar a mysql:
```
mysql
```

Y ejecuta los siguientes comandos:
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
## Paso 7: Importar Esquema y Datos Iniciales

En el host del servidor Zabbix, importe el esquema y los datos iniciales. Se le pedirá que ingrese su contraseña recién creada.
```
zcat /usr/share/zabbix-sql-scripts/mysql/server.sql.gz | mysql --default-character-set=utf8mb4 -uzabbix -p zabbix
```
## Paso 8: Configure la base de datos para el servidor Zabbix:

Edita el siguiente archivo `/etc/zabbix/zabbix_server.conf`, utiliza el editor nano:
```
nano /etc/zabbix/zabbix_server.conf
```

Busca la siguiente línea y reemplaza "password" por la clave real que configuraste en la base de datos.
> `DBPassword=password`

